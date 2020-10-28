## Minimum Remove to Make Valid Parentheses

## Solution:

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
