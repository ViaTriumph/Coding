Question: [https://leetcode.com/problems/coin-change-2/](https://leetcode.com/problems/coin-change-2/)
```kotlin
    fun change(amount: Int, coins: IntArray): Int {
        val maxComb = Array(coins.size){ IntArray(amount+1){0} }
        
        for(i in 0..coins.size-1){
            for(j in 0..amount){
                if(j == 0){
                    maxComb[i][j] = 1
                }else if(i == 0){
                    if(j >= coins[i]){
                        maxComb[i][j] = maxComb[i][j-coins[i]]
                    }
                }else if(j >= coins[i]){
                    maxComb[i][j] = maxComb[i-1][j] + maxComb[i][j-coins[i]]
                }else{
                    maxComb[i][j] = maxComb[i-1][j]
                }
            }
        }
        
        return maxComb[coins.size-1][amount]
    }
```
