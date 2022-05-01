Question: [https://leetcode.com/problems/kth-largest-element-in-a-stream/](https://leetcode.com/problems/kth-largest-element-in-a-stream/)
```kotlin
class KthLargest(k: Int, nums: IntArray) {
    val numsL = nums
    val kL = k
    val pq = PriorityQueue<Int>()
    
    init{
        init()
    }
    
    fun init(){
        for(num in numsL){
            pq.add(num)
            if(pq.size > kL){
                pq.poll()
            }
        }
    }
    
    fun add(`val`: Int): Int {
        pq.add(`val`)
        if(pq.size > kL){
            pq.poll()
        }
        
        return pq.peek()
    }

}
```
