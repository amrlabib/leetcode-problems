## Two Sum II - Input array is sorted

https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/


## Solution:

The idea in this problem is the fact that the array is sorted and this mean that if assign a pointer to the min value (first value) and a pointer to the max value (last value) and check if the sum is equal to target we can loop only once on the entire array to get the correct answer, if the values are equal we return the indexes if the sum is greater than the value we move the max pointer 1 index to the left if the value the sum is smaller we move the min pointer one index forward this way we can find the indexes with sum equal to target

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
