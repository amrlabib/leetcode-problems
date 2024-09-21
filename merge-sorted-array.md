# Merge Sorted Array

https://leetcode.com/problems/merge-sorted-array/

## Solution:


```javascript
var merge = function(nums1, m, nums2, n) {
    let i = 0;
    let j = 0;
    while(i < (m + n) && j < n) {
        if(nums1[i] < nums2[j] && i < (m + j)) {
            i++;
        } else if(nums1[i] >= nums2[j] && i < (m + j)) {
            nums1.splice(i,0, nums2[j]);
            nums1.pop();
            i++;
            j++;
        } else if (i >= (m + j)) {
            nums1.splice(i,0, nums2[j]);
            nums1.pop();
            i++;
            j++;
        } 
    }
};
```

## Solution:

```javascript
var merge = function(nums1, m, nums2, n) {
    let num1Pointer = m - 1;  
    let num2Pointer = n - 1;
    let currentPointer = m + n - 1;
    while (currentPointer >= 0) {
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
