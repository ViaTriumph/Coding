Question: [https://leetcode.com/problems/maximum-subarray/](https://leetcode.com/problems/maximum-subarray/)
```kotlin
    fun maxSubArray(nums: IntArray): Int {
        var i = 0
        var total = -10002
        var maxTotal = -10002
        for(j in 0..nums.size-1){
            if(nums[j] > total + nums[j]){
                total = nums[j]
                i = j
            }else {
                total = total + nums[j]
            }
            if(maxTotal < total){
                maxTotal = total
            }
        }
        return maxTotal
    }
```
