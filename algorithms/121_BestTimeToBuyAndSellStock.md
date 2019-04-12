## Problem

Say you have an array for which the `i`th element is the price of a given stock on day `i`.

If you were only permitted to complete at most one transaction (i.e., buy one and sell one share of the stock), design an algorithm to find the maximum profit.

Note that you cannot sell a stock before you buy one.

**Example 1:**
```
Input: [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
             Not 7-1 = 6, as selling price needs to be larger than buying price.
```

**Example 2:**
```
Input: [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e. max profit = 0.
```

**Description**
简单的DP问题

## Solution 
```
class Solution(object):
    def maxProfit(self, prices):
        if not prices:
            return 0
        max_profit = max_cur = 0
        for i in range(1,len(prices)):
            max_cur += prices[i] - prices[i - 1]
            max_cur = max(0, max_cur)
            max_profit = max(max_profit, max_cur)

        return max_profit
        
```
links:https://leetcode.com/problems/best-time-to-buy-and-sell-stock/
