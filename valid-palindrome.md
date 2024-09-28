# Valid Palindrome

https://leetcode.com/problems/valid-palindrome/description/

## Solution

```javascript
var isPalindrome = function(s) {
    let leftPointer = 0;
    let rightPointer = s.length - 1;
    let validChar = /[0-9a-zA-Z]/
    while (leftPointer < s.length && rightPointer >= 0) {
        let leftCharValid = validChar.test(s[leftPointer]);
        let rightCharValid = validChar.test(s[rightPointer]);
        !leftCharValid && leftPointer++;
        !rightCharValid && rightPointer--;

        if (leftCharValid && rightCharValid) {
            if (s[leftPointer].toLowerCase() === s[rightPointer].toLowerCase()) {
                leftPointer++;
                rightPointer--;
            } else {
                return false;
            }
        }
    }
    return true;
};
```
