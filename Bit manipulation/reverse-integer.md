Question: [https://leetcode.com/problems/reverse-integer/](https://leetcode.com/problems/reverse-integer/)
```kotlin
    fun reverse(x: Int): Int {
        var prev = 0
        var res = 0
        var n = x
        
        while(n != 0){
            res = res*10 + n%10
            if((res - n%10)/10 != prev){
                return 0
            }
            
            prev = res
            
            n /= 10
        }
        
        return prev
    }
```
