Question: [https://leetcode.com/problems/longest-common-subsequence/](https://leetcode.com/problems/longest-common-subsequence/)
```kotlin
    fun longestCommonSubsequence(text1: String, text2: String): Int {
        val m = text1.length
        val n = text2.length
        val matrix = Array(m){IntArray(n){0}}
        for(j in 0..n-1){
            if(text1[0] == text2[j]){
                matrix[0][j] = 1
            }else if(j > 0){
                matrix[0][j] = matrix[0][j-1]
            }
        }
        
        for(i in 0..m-1){
            if(text1[i] == text2[0]){
                matrix[i][0] = 1
            }else if(i > 0){
                matrix[i][0] = matrix[i-1][0]
            }
        }
        
        for(i in 1..m-1){
            for(j in 1..n-1){
                if(text1[i] == text2[j]){
                    matrix[i][j] = 1 + matrix[i-1][j-1]
                }else{
                    matrix[i][j] = maxOf(matrix[i-1][j], matrix[i][j-1])
                }
            }
        }
    
        
        return matrix[m-1][n-1]
    }
```
