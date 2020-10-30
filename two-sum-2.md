## Two Sum II - Input array is sorted

https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/

## Solution:

```javascript
/**
 * @param {number[]} numbers
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(numbers, target) {
    let leftIndex = 0;
    let rightIndex = numbers.length - 1;
    while(leftIndex !== rightIndex) {
        if(numbers[leftIndex] + numbers[rightIndex] === target) {
            return [leftIndex + 1, rightIndex + 1];
        }

        if(numbers[leftIndex] + numbers[rightIndex] > target) {
            rightIndex--;
        } else if (numbers[leftIndex] + numbers[rightIndex] < target) {
            leftIndex++;
        }
    }
};
```