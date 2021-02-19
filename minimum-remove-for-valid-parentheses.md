## Minimum Remove to Make Valid Parentheses

https://leetcode.com/problems/minimum-remove-to-make-valid-parentheses/

## Solution:

In this solution we use a stack data structure, we add every open parenthesis to the stack and we pop whenever we get a close parentheses, if a close parenthesis is found and stack is empty it means this close parenthesis should be removed, also if at the end of the scan we have any parenthesis in the stack they should be removed.

The stack is saving the index of the open parenthesis

```javascript
/**
 * @param {string} s
 * @return {string}
 */
var minRemoveToMakeValid = function(s) {
    const openParenthesis = [];
    const closeParenthesis = [];
    for (let i = 0; i < s.length; i++) {
        const currentChar = s[i];
        if (currentChar === '(') {
            openParenthesis.push(i);
        } else if (currentChar === ')') {
            if (openParenthesis.length > 0) {
                openParenthesis.pop();
            } else {
                closeParenthesis.push(i);
            }
        }
    }

    const indicesToBeRemoved = {};
    for (let i = 0; i < openParenthesis.length; i++) {
        indicesToBeRemoved[openParenthesis[i]] = true;
    }
    for (let i = 0; i < closeParenthesis.length; i++) {
        indicesToBeRemoved[closeParenthesis[i]] = true;
    }

    let finalString = '';
    for (let i = 0; i < s.length; i++) {
        if (indicesToBeRemoved[i]) {
            continue;
        }
        finalString += s[i];
    }
    return finalString;
};
```
