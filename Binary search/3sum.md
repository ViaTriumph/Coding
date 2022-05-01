Question: [https://leetcode.com/problems/3sum/](https://leetcode.com/problems/3sum/)
```kotlin
    fun threeSum(nums: IntArray): List<List<Int>> {
        val list = nums.sorted()
        val set = mutableSetOf<List<Int>>()
        for(i in 0..list.size-1){
            val k = -list[i]
            
            var a = i+1
            var b = list.size-1
            var sum = 0
            while(a<b){
                sum = list[a] + list[b]
                
                if(sum == k){
                    set.add(listOf(list[i], list[a], list[b]))
                    a++
                    b--
                }else if(sum < k){
                    a++
                }else{
                    b--
                }
            }
        }

        return set.toList()
    }
```
