## Two Sum

https://leetcode.com/problems/verifying-an-alien-dictionary/

## Solution:

We create a hash map from order string with key as the character and value as position, this will give us the ability to compare 2 characters and see if one of them fall before or after the other.

```javascript
/**
 * @param {string[]} words
 * @param {string} order
 * @return {boolean}
 */

function getOrderMap(order) {
    const orderMap = {};
    for (let i = 0; i < order.length; i++) {
        orderMap[order[i]] = i;
    }
    return orderMap;
}

var isAlienSorted = function(words, order) {
    const orderMap = getOrderMap(order);
    for (let i = 0; i < words.length - 1; i++) {
        const firstWord = words[i];
        const secondWord = words[i+1];
        const firstWordLength = firstWord.length;
        const secondWordLength = secondWord.length;
        const maxLength = firstWordLength > secondWordLength ? firstWordLength : secondWordLength;
        for (let j = 0; j < maxLength; j++) {
            const firstWordChar = firstWord[j];
            const secondWordChar = secondWord[j];
            if (orderMap[firstWordChar] > orderMap[secondWordChar] || secondWordChar === undefined) {
                return false;
            }

            if (orderMap[firstWordChar] < orderMap[secondWordChar] || firstWordChar === undefined) {
                break;
            }
        }
    }
    return true;
};
```