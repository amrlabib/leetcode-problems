## Longest Substring Without Repeating Characters

https://leetcode.com/problems/longest-substring-without-repeating-characters/

## Solution 1:

The solution of this probalem is based on 2 concepts, the first is sliding window where we keep track for the length on substrings while increasing the index, and the second is the use of an object or a hash map, where we can save the current window characters and be able to check if they exit or not in O(1) time, so we start from first index and we add the character to the map and we increase length by 1, after that we move forward by increasing window size by 1 and we make a check if the current index character is already in the hash map it means we have duplicate and we need to reset the length and decrease the window size by one character from the left.

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
