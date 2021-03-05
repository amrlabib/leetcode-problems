## Find First and Last Position of Element in Sorted Array

https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/


### Solution:

The solution is based on binary search the idea is to run binary search with very little change that will make sure that we get the left most target value and this will be the start index, the we run another round of binary from that left most index to the rest of the array with the minor change that will make sure that we get the last index of the target.


```javascript
var searchRange = function(nums, target) {
    let left = 0;
    let right = nums.length - 1;
    let mid = Math.floor(left + ((right - left) / 2));
    let startIndex = -1;
    while (left != right && left < right) {
        if (nums[mid] === target && nums[mid - 1] !== target) {
            startIndex = mid;
            break;
        } else if (nums[mid] < target) {
            left = mid + 1;
        } else if (nums[mid] > target || nums[mid - 1] === target) {
            right = mid - 1;
        }
        mid = Math.floor(left + ((right - left) / 2));
    }

    if (left === right && nums[left] === target) {
        startIndex = left;
    }

    if (startIndex === -1) {
        return [-1, -1];
    }

    right = nums.length - 1;
    mid = Math.floor(left + ((right - left) / 2));
    let endIndex = -1;
    while (left != right && left < right) {
        if (nums[mid] === target && nums[mid + 1] !== target) {
            endIndex = mid;
            break;
        } else if (nums[mid] < target || nums[mid + 1] === target) {
            left = mid + 1;
        } else if (nums[mid] > target) {
            right = mid - 1;
        }
        mid = Math.floor(left + ((right - left) / 2));
    }

    if (left === right && nums[right] === target) {
        endIndex = right;
    }

    return [startIndex, endIndex];
};
```