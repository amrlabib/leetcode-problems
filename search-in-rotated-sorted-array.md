## Search in rotated sorted array

https://leetcode.com/problems/search-in-rotated-sorted-array/

### Solution:

The problem is the find the target number in log(n) time in sorted array, this will mean that we need to find the target using binary search the only issue is that the sorted array is rotated at an unknown index, so to be able to use binary search we need to find first the position where the sorted array is rotated, and then decide if target will be the right or left partition of that position.

1. To be able to find the rotated position we just need to find the smallest value in the array, we can do that using binary search as well with minor change in the conditions to put into consideration the rotation
2. After finding the rotation index (min value index) we just need to decide if the target value is in right hand side of the rotation position or left hand side
3. We use binary search on the right partion of the array to find the target

```javascript
function getMinValueIndex(nums) {
    let left = 0;
    let right = nums.length - 1;
    let mid = Math.floor(left + ((right - left) / 2));
    while (left != right) {
        if (nums[mid] > nums[right]) {
            left = mid + 1;
        } else if(nums[mid] < nums[mid+1] && nums[mid] < nums[mid-1]) {
            return mid;
        } else {
            right--;
        }
        mid = Math.floor(left + ((right - left) / 2));
    }

    if (left === right) {
        return left;
    }
}

function search(nums, target) {
    const minValueIndex = getMinValueIndex(nums);
    let left = 0;
    let right = nums.length - 1;
    let mid = Math.floor(left + ((right - left) / 2));
    if (target >= nums[minValueIndex] && target <= nums[right]) {
        left = minValueIndex;
        mid = Math.floor(left + ((right - left) / 2));
    } else {
        right = minValueIndex - 1;
        mid = Math.floor(left + ((right - left) / 2));
    }
    while (left != right && left < right && left < nums.length && right >= 0) {
        if (target === nums[mid]) {
            return mid;
        } else if (target > nums[mid]) {
            left = mid + 1;
        } else if (target < nums[mid]) {
            right = mid - 1;
        }
        mid = Math.floor(left + ((right - left) / 2));
    }

    if (left === right && target === nums[mid])
        return mid;

    return -1;
};
```