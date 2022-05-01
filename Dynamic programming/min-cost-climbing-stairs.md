Question: [https://leetcode.com/problems/min-cost-climbing-stairs/](https://leetcode.com/problems/min-cost-climbing-stairs/)
```kotlin
    fun minCostClimbingStairs(cost: IntArray): Int {
        val minC = IntArray(cost.size+1){Int.MAX_VALUE}
        minC[0] = 0
        minC[1] = 0
        
        for(i in 2..cost.size){
            minC[i] = minOf(minC[i-1] + cost[i-1], minC[i-2] + cost[i-2])
        }
        
        return minC[cost.size]
    }
```
