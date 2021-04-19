## Longest Valid Parentheses

https://leetcode.com/problems/longest-valid-parentheses/

## Solution:

In this solution we will use a stack to keep track of valid open and close parentheses, for each '(' we push current string length to the stack and whenever we reach a ')' we pop one item from the stack and increment the currentLength.

This propblem is very similar to the minimum remove from parantheses to get valid string, with a small change where we need to keep track of current valid length inside each cell of the stack, and we calculate the current iteration length based on current length - the top item inside the stack if it exist.

```javascript
var longestValidParentheses = function(s) {
    let open = [];
    let maxLength = 0;
    let currentLength = 0;
    for (let i = 0; i < s.length; i++) {
        if (s[i] === '(') {
            open.push(currentLength);
        } else if(s[i] === ')' && open.length > 0) {
            open.pop();
            currentLength++;
        } else if (s[i] === ')' && open.length === 0) {
            currentLength = 0;
        }

        if (currentLength - (open[open.length - 1] || 0) > maxLength) {
           maxLength = currentLength - (open[open.length - 1] || 0);
        }
    }

    return maxLength * 2;
};
```