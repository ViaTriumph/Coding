Question: [https://leetcode.com/problems/valid-anagram/](https://leetcode.com/problems/valid-anagram/)
```kotlin
fun isAnagram(s: String, t: String): Boolean {
        if(s.length != t.length) return false
        val htable = IntArray(26){0}
        for(i in 0..t.length-1){
            htable[s[i] - 'a']++
            htable[t[i] - 'a']--
        }
        for(i in 0..25){
            if(htable[i]!=0) return false
        }
        return true
}
```
