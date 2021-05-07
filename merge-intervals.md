## Merge Intervals

https://leetcode.com/problems/merge-intervals/

## Solution

The solution is to first sort the intervals based on start time and then loop once to merge overlapping intervals

```javascript
function getSortedIntervals(intervals) {
    return intervals.sort((first, second) => {
        if(first[0] < second[0]) {
            return -1;
        } else if (first[0] > second[0]) {
            return 1;
        } else if (first[1] < second[1]) {
            return -1;
        } else if (first[1] > second[1]) {
            return 1;
        }
        return 0;
    });
}

var merge = function(nonSortedIntervals) {
    const intervals = getSortedIntervals(nonSortedIntervals);
    const newMergedIntervals = [intervals[0]];
    let index = 0;
    for (let i = 1; i < intervals.length; i++) {
        if (intervals[i][0] <= newMergedIntervals[index][1]) {
            newMergedIntervals[index] = [newMergedIntervals[index][0], Math.max(newMergedIntervals[index][1], intervals[i][1])];
        } else if (intervals[i][0] > newMergedIntervals[index][1]) {
            newMergedIntervals[++index] = intervals[i];
        }
    }
    return newMergedIntervals;
};
```