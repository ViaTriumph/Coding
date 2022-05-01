Question: [https://leetcode.com/problems/product-of-array-except-self/](https://leetcode.com/problems/product-of-array-except-self/)
```kotlin
    fun productExceptSelf(nums: IntArray): IntArray {
        var mul: Long = 1
        var zeroIndex = -1
        var isZero = false
        var zeroCount = 0
        
        for(i in 0..nums.size-1){
            isZero = nums[i] == 0
            if(isZero){
                zeroCount++
                zeroIndex = i
                continue
            }
            mul *= nums[i]
        }
        
        if(zeroCount > 1){
            for(i in 0..nums.size-1){
                nums[i] = 0
            }
        }else if(zeroCount == 1){
            for(i in 0..nums.size-1){
                nums[i] = 0
            }
            nums[zeroIndex] = mul.toInt()
        }else{
            for(i in 0..nums.size-1){
                nums[i] = (mul/nums[i]).toInt()
            }
        }
        
        
        return nums
    }
```
