## Remove Duplicates from Sorted Array

https://leetcode.com/problems/remove-duplicates-from-sorted-array/

## Solution:

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var removeDuplicates = function(nums) {
    let similarValueLength = 0;
    for (let i = 1; i < nums.length; i++) {
        if (nums[i] === nums[i-1]) {
            similarValueLength++;
        }
        
        if((nums[i] !== nums[i-1] || i === nums.length - 1) && similarValueLength > 0) {
            nums.splice(i - similarValueLength, similarValueLength);
            i = i - similarValueLength;
            similarValueLength = 0;
        }
    }
};
```