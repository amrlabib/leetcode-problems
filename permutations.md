## Permutations:

https://leetcode.com/problems/permutations/

## Solution:

The Solution is based on recursion, where we loop on list of items in the list and then we remove that item and call the permutation function again with the new array where that new array is missing the previous item


```javascript
function permuteNums(nums, currentChars, result) {
    for (let i = 0; i < nums.length; i++) {
        if (nums.length > 0) {
            const newNums = [...nums];
            newNums.splice(i, 1);
            permuteNums(newNums, [...currentChars, nums[i]], result);
        }
    }
    if (nums.length === 0) {
        result.push(currentChars);
    }
}

var permute = function(nums) {
    const result = [];
    permuteNums(nums, [], result);
    return result;
};
```