# Merge Sorted Array

https://leetcode.com/problems/merge-sorted-array/


## Solution:

In this solution we use 2 pointers starting at the end of each array, and we compare the values. The reason we start at the end is to take advantage of nums1 empty zeros as we know the 2 arrays are sorted we can add the values backward to be able to fill the empty zeros locations first. In this solution the time complexity is O (m + n)

```javascript
var merge = function(nums1, m, nums2, n) {
    let num1Pointer = m - 1;  
    let num2Pointer = n - 1;
    let currentPointer = m + n - 1;
    while (currentPointer >= 0 && num2Pointer >= 0) {
        if (nums2[num2Pointer] > nums1[num1Pointer] || num1Pointer < 0) {
            nums1[currentPointer] = nums2[num2Pointer];
            num2Pointer--;
        } else {
            nums1[currentPointer] = nums1[num1Pointer];
            num1Pointer--;
        }
        currentPointer--;
    }
};
```
