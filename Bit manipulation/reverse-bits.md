Question: [https://leetcode.com/problems/reverse-bits/](https://leetcode.com/problems/reverse-bits/)
```kotlin
    // you need treat n as an unsigned value
    fun reverseBits(n:Int):Int {
        var a = n.toUInt()
        var num = 0.toUInt()
        var countedBits = 0
        
        
        while(a > 0U){
            num += (a and 1.toUInt())
            
            a = a.shr(1)
            if(a > 0U){
               num = num.shl(1) 
            } 
            
            countedBits++
        }
        
        while(countedBits < 32){
            num = num.shl(1)
            countedBits++
        }

        
        return num.toInt()
    }
```
