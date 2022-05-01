Question: [https://leetcode.com/problems/climbing-stairs/](https://leetcode.com/problems/climbing-stairs/)
```kotlin
    fun climbStairs(n: Int): Int {
        return solve(n)
    }
    
    fun solve(n: Int): Int{
        val distinct = IntArray(n+1)
        if(n == 0){
            return 0
        }else if(n == 1){
            return 1
        }else if(n == 2){
            return 2
        }
        
        distinct[0] = 0
        distinct[1] = 1
        distinct[2] = 2
        
        for(i in 3..n){
            distinct[i] = distinct[i-1] + distinct[i-2]
        }
        
        return distinct[n]
    }
```
