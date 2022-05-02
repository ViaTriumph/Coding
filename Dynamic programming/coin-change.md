Question: [https://leetcode.com/problems/coin-change/](https://leetcode.com/problems/coin-change/)
```kotlin
    fun coinChange(coins: IntArray, amount: Int): Int {
        val m = Array(coins.size){IntArray(amount+1){-1}}
        for(j in 0..amount){
            if(coins[0] > j){
                continue
            }else{
                if(j%(coins[0]) == 0){
                    m[0][j] = j/coins[0] // coins[i] won't be zero
                }
            }
        }
        
        for(i in 0..coins.size-1){
            m[i][0] = 0
        }
        
        for(i in 1..coins.size-1){
            for(j in 1..amount){
                if(j >= coins[i]){
                    m[i][j] = if(m[i-1][j] != -1 && m[i][j-coins[i]] != -1){
                        minOf(m[i-1][j], 1 + m[i][j-coins[i]])
                    }else if(m[i-1][j] != -1 && m[i][j-coins[i]] == -1){
                        m[i-1][j]
                    }else if(m[i-1][j] == -1 && m[i][j-coins[i]] != -1){
                        1 + m[i][j-coins[i]]
                    }else{
                        -1
                    }
                }else{
                    m[i][j] = m[i-1][j]
                }
            }
        }
        return  m[coins.size-1][amount] 
    }
```
