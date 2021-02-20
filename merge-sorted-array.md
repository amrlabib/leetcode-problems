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
