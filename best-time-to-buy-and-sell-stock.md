## Best Time to Buy and Sell Stock

https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

## Solution:

The solution is based on kadane's algorithm that can return the max sum of subarray, the only difference is that in this problem we need to calculate the diff between adjacent indexes and then we can calculate the max sum subarray and this sum is the max profit

```javascript
var maxProfit = function(prices) {
    let max = 0;
    let currentMax = 0;
    for (let i = 1; i < prices.length; i++) {
        const diff = prices[i] - prices[i - 1];
        currentMax = Math.max(diff, currentMax + diff);
        if (currentMax > max) {
            max = currentMax;
        }
    }
    return max;
};
```