Question: [https://leetcode.com/problems/counting-bits/](https://leetcode.com/problems/counting-bits/)
```kotlin
class Solution {
    
    val list = IntArray(100001){0}
    
    init{
        initList()
    }
    
    fun initList(){
       for(i in 0..100000) {
           list[i] = countB(i)
       }
    }
    
    fun countB(n: Int): Int {
        var count = 0
        var num = n
        while(num > 0){
            count += (num and 1)
            num = num shr 1
        }
        
        return count
    }
    
    fun countBits(n: Int): IntArray {
        return list.copyOfRange(0,n+1)
    }
}
```
