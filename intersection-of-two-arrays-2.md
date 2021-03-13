## Intersection of Two Arrays II

https://leetcode.com/problems/intersection-of-two-arrays-ii/

### Solution:

```javascript
var intersect = function(nums1, nums2) {
    const nums1Map = {};
    for (let i = 0; i < nums1.length; i++) {
        nums1Map[nums1[i]] ? nums1Map[nums1[i]]++ : nums1Map[nums1[i]] = 1;
    }

    const nums2Map = {};
    for (let i = 0; i < nums2.length; i++) {
        nums2Map[nums2[i]] ? nums2Map[nums2[i]]++ : nums2Map[nums2[i]] = 1;
    }

    const resultArray = [];
    Object.keys(nums2Map).forEach((key) => {
        let numberOfTimesToAdd = 0;
        if (nums1Map[key] && nums2Map[key] && nums1Map[key] <= nums2Map[key]) {
           numberOfTimesToAdd = nums1Map[key];
        } else if (nums1Map[key] && nums2Map[key] && nums1Map[key] > nums2Map[key]) {
           numberOfTimesToAdd = nums2Map[key];
        }
        for (let i = 0; i < numberOfTimesToAdd; i++) {
            resultArray.push(key);
        }
    });

    return resultArray;
};
```