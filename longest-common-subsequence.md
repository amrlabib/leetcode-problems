## Longest Common Subsequence

https://leetcode.com/problems/longest-common-subsequence/

### solution:

using recursion and dynamic programming where we memoize the result for know recursive steps and use them later

```javascript
var longestCommonSubsequence = function(text1, text2) {
    const memoizedLCS = {};
    function lcs (text1, text2, i, j) {
        if (memoizedLCS[`${i}-${j}`] !== undefined) {
            return memoizedLCS[`${i}-${j}`];
        }

        let result = 0;
        if (i < 0 || j < 0) {
            result = 0;
        } else if (text1[i] === text2[j]) {
            result = lcs(text1, text2, i - 1, j - 1) + 1;
        } else {
            const res1 = lcs(text1, text2, i, j - 1);
            const res2 = lcs(text1, text2, i - 1, j);
            result = Math.max(res1, res2);
        }
        memoizedLCS[`${i}-${j}`] = result;
        return result;
    }
    return lcs(text1, text2, text1.length - 1, text2.length - 1);
};
```