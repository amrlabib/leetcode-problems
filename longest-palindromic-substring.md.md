## Longest Palindromic Substring

https://leetcode.com/problems/longest-palindromic-substring/

## Solution:

This based brute-force solution is based on taking an index and keep moving left and right pointers from that index, if left and right pointers characters are the same then it is palindromic substring, in this solution we need to handle the special case where consecutive characters will be similar and in that case we need to move the right pointer only until we reach a different character

```javascript
var longestPalindrome = function(s) {
    let maxLength = 0;
    let finalVal = '';
    if (s.length === 1) {
        return s;
    }
    for(let i = 0; i < s.length; i++) {
        let left = i - 1;
        let right = i + 1;
        let length = 1;
        let val = s[i];
        if (length > maxLength) {
            maxLength = length;
            finalVal = val;
        }
        while (right < s.length && s[right] === s[i]) {
            length++;
            val = val + s[right];
            if (length > maxLength) {
                maxLength = length;
                finalVal = val;
            }
            right++;
        }
        while (left >= 0 && right < s.length && s[left] === s[right]) {
            length += 2;
            val = s[left] + val + s[right];
            if (length > maxLength) {
                maxLength = length;
                finalVal = val;
            }

            left--;
            right++;
        }
    }
    return finalVal;
};
```
