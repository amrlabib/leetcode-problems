## Permutations 2:

https://leetcode.com/problems/permutations-ii/

## Solution:

```javascript
function permuteNums(nums, currentChars, result) {
    let used = {};
    for (let i = 0; i < nums.length; i++) {
        if (used[nums[i]]) {
            continue;
        }

        if (nums.length > 0) {
            const newNums = [...nums];
            newNums.splice(i, 1);
            permuteNums(newNums, [...currentChars, nums[i]], result);
        }
        used[nums[i]] = true;
    }
    if (nums.length === 0) {
        result.push(currentChars);
    }
}


var permuteUnique = function(nums) {
    const result = [];
    permuteNums(nums, [], result);
    return result;
};
```