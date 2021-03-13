## Intersection of Two Arrays

https://leetcode.com/problems/intersection-of-two-arrays/

### Solution:

```javascript
var intersection = function(nums1, nums2) {
    let firstArrMap = {};
    for (let i = 0; i < nums1.length; i++) {
        firstArrMap[nums1[i]] = true;
    }

    let intersectionMap = {};
    for(let i = 0; i< nums2.length; i++) {
        if (firstArrMap[nums2[i]]) {
           intersectionMap[nums2[i]] = true;
        }
    }

    let finalArray = [];
    Object.keys(intersectionMap).forEach(key => finalArray.push(key));

    return finalArray;
};
```