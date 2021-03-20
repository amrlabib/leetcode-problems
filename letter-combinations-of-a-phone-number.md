## letter-combinations-of-a-phone-number.md

https://leetcode.com/problems/letter-combinations-of-a-phone-number/

## Solution:

```javascript
function getCharsForNumber(number) {
    return {
        '2': ['a', 'b', 'c'],
        '3': ['d', 'e', 'f'],
        '4': ['g', 'h', 'i'],
        '5': ['j', 'k', 'l'],
        '6': ['m', 'n', 'o'],
        '7': ['p', 'q', 'r', 's'],
        '8': ['t', 'u', 'v'],
        '9': ['w', 'x' , 'y', 'z']
    }[number];
}

function getCombinations(digits, currentCombChar, result) {
    const currentChars = getCharsForNumber(digits[0]);
    const digitsLength = digits.length;
    for (let j = 0; j < currentChars.length; j++) {
        const comb = currentCombChar + currentChars[j];
        if (digitsLength === 1) {
            result.push(comb);
        } else {
            getCombinations(digits.slice(1), comb, result);
        }
    }
}

var letterCombinations = function(digits) {
    let result = [];
    if (digits.length > 0) {
        getCombinations(digits, '', result);
    }
    return result;
};
```