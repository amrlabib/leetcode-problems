##  Best Time to Buy and Sell Stock II

https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/

## Solution:

Solution is to calculate the diff between each adjacent prices and sum all diff values that is greater than 0

```javascript
var maxProfit = function(prices) {
    let max = 0;
    for (let i = 1; i < prices.length; i++) {
        const diff = prices[i] - prices[i-1];
        if (diff > 0) {
           max+= diff;
        }
    }
    return max;
};
```