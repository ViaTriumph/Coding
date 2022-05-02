Question: [https://leetcode.com/problems/decode-ways/](https://leetcode.com/problems/decode-ways/)
```kotlin
    fun numDecodings(s: String): Int {
        val decode = IntArray(s.length){0}
        if(s[0] != '0'){
            decode[0] = 1
        }
        
        for(i in 1..s.length-1){
            if(s[i] != '0'){
                decode[i] = decode[i-1]
            }
            if(s[i-1] != '0' && (""+s[i-1]+s[i]).toInt() <= 26){
                if(i > 1){
                    decode[i] += decode[i-2]
                }else{
                    decode[i]++
                }
            }
        }
        
        return decode[s.length-1]
    }
```
