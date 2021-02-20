## 3Sum:

https://leetcode.com/problems/3sum/

## Solution:

This solution will use the window sliding for sorted array, and apply it for each item so the solution will be O(n^2), first we sort the array, then we loop on each element, and for each element we loop through the rest of the array using the sliding window technique, this way the problem is changed to be 2 sum problem with one extra number which will cause the n^2 complexity

```javascript
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var threeSum = function(nums) {
    nums.sort(function(a, b){return a - b});
    const resultArray = [];
    for (let i = 0 ; i < nums.length; i++) {
        if(nums[i] > 0) {
            break;
        }
        const currentValue = nums[i];
        if (i !== 0 && nums[i] === nums[i-1]) {
            continue;
        }
        let leftIndex = i + 1;
        let rightIndex = nums.length - 1;
        while (leftIndex < rightIndex) {
            const sumValue = currentValue + nums[leftIndex] + nums[rightIndex];
            if (sumValue < 0) {
                leftIndex++;
            } else if (sumValue > 0){
                rightIndex--;
            } else {
                resultArray.push([currentValue, nums[leftIndex], nums[rightIndex]]);
                leftIndex++;
                rightIndex--;
                while(leftIndex < rightIndex && nums[leftIndex] === nums[leftIndex - 1]) {
                    leftIndex++;
                }
                while(leftIndex < rightIndex && nums[rightIndex] === nums[rightIndex + 1]) {
                    rightIndex--;
                }
            }
        }
    }
    return resultArray;
};
```
