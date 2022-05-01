Question: [https://leetcode.com/problems/top-k-frequent-elements/](https://leetcode.com/problems/top-k-frequent-elements/)
```kotlin
    fun topKFrequent(nums: IntArray, k: Int): IntArray {
        val pq = PriorityQueue<Pair<Int, Int>>{a,b -> b.second-a.second}
        val map = hashMapOf<Int, Int>()
        val list = mutableListOf<Int>()
        
        for(i in 0..nums.size-1){
            if(map[nums[i]] == null){
                map[nums[i]] = 1
            }else{
                map[nums[i]] = map[nums[i]]!! + 1
            }
        }
        var cutOff = k
        for((key, value) in map){
            pq.add(Pair(key, value))
        }
        
        while(pq.size > 0){
            if(cutOff <= 0){
                break
            }
            val top = pq.poll()
            list.add(top!!.first)
            cutOff--
        }
        
        return list.toIntArray()
    }
```
