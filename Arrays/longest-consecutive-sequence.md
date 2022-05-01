Question: [https://leetcode.com/problems/longest-consecutive-sequence/](https://leetcode.com/problems/longest-consecutive-sequence/)
```kotlin
    fun longestConsecutive(nums: IntArray): Int {
        val pq = PriorityQueue<Int>()
        
        for(i in nums){
            pq.add(i)
        }
        
        var count = 0
        var maxC = 0
        var prev = Int.MIN_VALUE
        while(!pq.isEmpty()){
            val top = pq.poll()
            if(prev == Int.MIN_VALUE){
                count = 1
                maxC = 1
            }else if(top == prev){
                continue
            }else if(top == prev + 1){
                count++
            }else{
                count = 1
            }
            prev = top
            maxC = maxOf(maxC, count)
        }
        
        return maxC
    }
```
