Question: [https://leetcode.com/problems/best-time-to-buy-and-sell-stock/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
```kotlin
    fun maxProfit(prices: IntArray): Int {
        val maxPeak = IntArray(prices.size){Int.MIN_VALUE}
        for(i in prices.size-1 downTo 0){
            if( i == prices.size - 1){
                maxPeak[i] = prices[i]
            }else{
                maxPeak[i] = maxOf(maxPeak[i+1], prices[i])
            }
        }
        var maxProfit = 0
        for(i in 0 .. prices.size-1){
            maxProfit = maxOf(maxProfit, maxPeak[i] - prices[i])
        }
        return maxProfit
    }
```
