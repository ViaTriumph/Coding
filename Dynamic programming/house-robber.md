Question: [https://leetcode.com/problems/house-robber/](https://leetcode.com/problems/house-robber/)
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
        
        for(i in 2..nums.size-1){
            rob[i] = maxOf(rob[i-2] + nums[i], rob[i-1])
        }
        return rob[nums.size-1]
    }
```
