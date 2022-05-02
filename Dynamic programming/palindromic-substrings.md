Question: [https://leetcode.com/problems/palindromic-substrings/](https://leetcode.com/problems/palindromic-substrings/)
```kotlin
    fun countSubstrings(s: String): Int {
        var c = 0
        var r = 0
        var mirror = 0
        val st = s.toCharArray().joinToString("#","#","#")
        val lps = IntArray(st.length){0}
        
        for(i in 0..st.length-1){
            mirror = 2*c - i
            if(r > i){
                lps[i] = minOf(r-i, lps[mirror])
            }else{
                lps[i] = 0
            }
            try{
                while(st[i+1+lps[i]] == st[i-1-lps[i]]){
                    lps[i]++
                }
            }catch(e: Exception){
                continue
            }
            
            if(i+lps[i] > r){
                r = i+lps[i]
                c = i
            }
        }
        var count = 0
        for(i in 0..lps.size-1){
            if(lps[i] > 0){
                count += Math.ceil(lps[i].toDouble()/2).toInt()
            }
        }
        
        return count
    }
```
