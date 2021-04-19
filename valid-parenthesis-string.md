## Valid Parenthesis String

https://leetcode.com/problems/valid-parenthesis-string/

## Solution:


```javascript
var checkValidString = function(s) {
    const open = [];
    const star = [];
    for (let i = 0; i < s.length; i++) {
        if (s[i] === '(') {
            open.push(i);
        } else if (s[i] === ')' && open.length > 0) {
            open.pop();
        } else if (s[i] === ')' && open.length === 0) {
            if (star.length > 0) {
                star.pop();
            } else {
                return false;
            }
        } else if (s[i] === '*') {
            star.push(i);
        }
    }

    for (let i = open.length - 1; i >= 0; i--) {
        if (star.length > 0 && open[i] < star[star.length - 1]) {
            star.pop();
        } else {
            return false;
        }
    }

    return true;
};
```