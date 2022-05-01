Question: [https://leetcode.com/problems/number-of-1-bits/](https://leetcode.com/problems/number-of-1-bits/)
```kotlin
    // you need treat n as an unsigned value
    fun hammingWeight(n:Int):Int {
        var num = n
        var count = 0
        if((num and -2147483648) != 0){
            count++
            num = num xor -2147483648
        }
        while(num > 0){
            if(num%2==1){
                count++
            }
            num = num shr 1
        }
        return count
    }
```
