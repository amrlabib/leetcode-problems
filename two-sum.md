## Two Sum

https://leetcode.com/problems/two-sum/

## Solution 1 O(2n):

Using hash map where the key is the value of each array index value, and the value is the index, we will loop on all array elements and check if (target - element value) exist in the hash map 

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    const numMap = {};
    for (let i = 0; i < nums.length; i++) {
        numMap[nums[i]] = i;
    }

    const resultArray = [];
    for (let i = 0; i < nums.length; i++) {
        const valueRequired = target - nums[i];
        if (numMap[valueRequired] !== undefined && numMap[valueRequired] !== i) {
            resultArray[0] = i;
            resultArray[1] = numMap[valueRequired];
            break;
        }
    }
    return resultArray;
};
```

## Solution 2 O(n^2):

Brute force solution, for each element in the array we will loop on all other elements and check if both elements sum is equal to target.


```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    const resultArray = [];
    for (let i = 0; i < nums.length; i++) {
        for (let j = 0; j < nums.length; j++) {
            if(i !== j && nums[i] + nums[j] === target) {
                resultArray[0] = i;
                resultArray[1] = j;
                break;
            }
        }
        if (resultArray.length > 0) {
            break;
        }
    }
    return resultArray;
};
```
