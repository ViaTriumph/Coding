Question: [https://leetcode.com/problems/unique-paths/](https://leetcode.com/problems/unique-paths/)
```kotlin
    fun uniquePaths(m: Int, n: Int): Int {
        val grid = Array(m){ IntArray(n){0} }
        
        for(i in 0..m-1){
            for(j in 0..n-1){
                if(i == 0 || j == 0){
                    grid[i][j] = 1
                    continue
                }
                if(i > 0){
                    grid[i][j] += grid[i-1][j]
                }
                if(j > 0){
                    grid[i][j] += grid[i][j-1]
                }
            }
        }
        return grid[m-1][n-1]
    }
```
