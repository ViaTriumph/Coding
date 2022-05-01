Question: [https://leetcode.com/problems/valid-palindrome/](https://leetcode.com/problems/valid-palindrome/)
```kotlin
fun isPalindrome(s: String): Boolean {
        var str = ""
        for(i in 0..s.length-1){
            if( (s[i] >= 'A' && s[i] <= 'Z') 
               || (s[i] >= 'a' && s[i] <= 'z') 
               || (s[i] >= '0' && s[i] <= '9')
              ){
                str += s[i]
            } 
        }
        var i = 0
        var j = str.length-1
        while(i<j){
            if(!str[i].equals(str[j], ignoreCase = true)){
                return false
            }
            i++
            j--
        }
        
        return true
}
```
