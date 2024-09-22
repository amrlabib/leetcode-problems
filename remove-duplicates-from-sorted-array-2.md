## Remove Duplicates from Sorted Array II

https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/description/

## Solution:

```javascript
var removeDuplicates = function(nums) {
    const maxDuplicateAllowed = 1;
    const length = nums.length
    let lastValidPointer = -1;
    let numValue = undefined;
    let numAppearCount = undefined;
    for (let i = 0; i < length; i++) {
        if (nums[i] === numValue) {
            numAppearCount++;
            if (numAppearCount > maxDuplicateAllowed) {
                continue;
            }
        } else if (nums[i] !== numValue) {
            numValue = nums[i];
            numAppearCount = 1;
        }

        lastValidPointer++;
        nums[lastValidPointer] = nums[i];
    }
    return (lastValidPointer + 1) ?? nums.length;
};
```


---


```javascript
var removeDuplicates = function(nums) {
    const length = nums.length
    let lastValidPointer = -1;
    let numValue = undefined;
    let numAppearCount = undefined;
    for (let i = 0; i < length; i++) {
        if (nums[i] === numValue) {
            numAppearCount++;
            if (numAppearCount > 2) {
                continue;
            }
        } else if (nums[i] !== numValue) {
            numValue = nums[i];
            numAppearCount = 1;
        }

        lastValidPointer++;
        nums[lastValidPointer] = nums[i];
    }
    return (lastValidPointer + 1) ?? nums.length;
};
```
