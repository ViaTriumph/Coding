Question: [https://leetcode.com/problems/longest-palindromic-substring/](https://leetcode.com/problems/longest-palindromic-substring/)
```kotlin
    fun longestPalindrome(s: String): String {
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
                c = i
                r = i+lps[i]
            }
        }
        c = 0
        r = 0
        for(i in 0..lps.size-1){
            if(r < lps[i]){
                r = lps[i]
                c = i
            }
        }
        return  st.substring(c-r, c+r+1).replace("#","")
    }
```
