## Longest

https://leetcode.com/problems/longest-substring-without-repeating-characters/

## Solution 1:

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
    let maxLength = 0;
    let currentLength = 0;
    let currentExistingChars = {};
    let i = 0;
    while(i < s.length) {
        const char = s[i];
        const charExistingIndex = currentExistingChars[char];
        if (charExistingIndex !== undefined) {
            currentLength = 0;
            currentExistingChars = {};
            i = charExistingIndex + 1;
            continue;
        } else {
            currentLength++;
        }

        currentExistingChars[char] = i;
        if(currentLength > maxLength) {
            maxLength = currentLength;
        }
        i++;
    }
    return maxLength;
};
```