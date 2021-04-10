## Longest Common Prefix

https://leetcode.com/problems/longest-common-prefix/

### Solution

```javascript
var longestCommonPrefix = function(strs) {
    let prefix = "";
    const strsLength = strs.length;
    if (strsLength === 0) {
        return prefix;
    }

    let j = 0;
    let firstStrLength = strs[0].length;
    while (j < firstStrLength) {
        let foundInvalidChar = false;
        for (let i = 1; i < strsLength; i++) {
            if(strs[i][j] !== strs[0][j]) {
                foundInvalidChar = true;
                break;
            }
        }

        if (foundInvalidChar) {
            return prefix;
        }
        prefix += strs[0][j];
        j++;
    }

    return prefix;
};
```