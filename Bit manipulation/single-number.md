Question: [https://leetcode.com/problems/single-number/](https://leetcode.com/problems/single-number/)
```kotlin
    fun singleNumber(nums: IntArray): Int {
        if(nums.size == 1){
            return nums[0]
        }
        var singleNo = nums[0]
        for(i in 1..nums.size-1){
            singleNo = singleNo xor nums[i]
        }
        return singleNo
    }
```
