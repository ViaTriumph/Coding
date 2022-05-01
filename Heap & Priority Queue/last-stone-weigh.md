Question: [https://leetcode.com/problems/last-stone-weight/](https://leetcode.com/problems/last-stone-weight/)
```kotlin
    fun lastStoneWeight(stones: IntArray): Int {
        if(stones.size == 1){
            return stones[0]
        }
        
        val pq = PriorityQueue<Int>{a,b -> b-a}
        
        
        for(stone in stones){
            pq.add(stone)
        }
        
        var y = 0
        var x = 0
        while(pq.size > 1){
            y = pq.poll()
            x = pq.poll()
            
            //SMAAAASH THE ROCKS
            
            if(y != x){
                pq.add(y-x)
            }
        }
        
        return if(pq.size == 1){
            pq.poll()
        }else{
            0
        }
    }
```
