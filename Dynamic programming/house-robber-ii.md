Question: [https://leetcode.com/problems/house-robber-ii/](https://leetcode.com/problems/house-robber-ii/)
```kotlin
    fun rob(nums: IntArray): Int {
        if(nums.size == 0){
            return 0
        }else if(nums.size == 1){
            return nums[0]
        }else if(nums.size == 2){
            return maxOf(nums[0], nums[1])
        }
        val rob = IntArray(nums.size){0}
        rob[0] = nums[0]
        rob[1] = maxOf(nums[0],nums[1])
        
        for(i in 2..nums.size-2){
            rob[i] = maxOf(rob[i-2] + nums[i], rob[i-1])
        }
        
        val rob2 = IntArray(nums.size){0}
        rob2[0] = Int.MIN_VALUE
        rob2[1] = nums[1]
        rob2[2] = maxOf(nums[1], nums[2])
        
        for(i in 3..nums.size-1){
            rob2[i] = maxOf(rob2[i-2]+nums[i], rob2[i-1])
        }
        
        return maxOf(rob2[nums.size - 1], rob[nums.size - 2])
    }
```
