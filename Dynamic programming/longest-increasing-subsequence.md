Question: [https://leetcode.com/problems/longest-increasing-subsequence/](https://leetcode.com/problems/longest-increasing-subsequence/)
```kotlin
    fun lengthOfLIS(nums: IntArray): Int {
        val d = mutableListOf<Int>()
        var index = 0
        d.add(nums[0])
        for(i in 1..nums.size-1){
            if(nums[i] > d.last()){
                d.add(nums[i])
            }else{
                index = lowerBound(d, nums[i])
                d[index] = nums[i]
            }
        }
        
        return d.size        
    }
    
    fun lowerBound(nums: MutableList<Int>, target: Int): Int{
        var i = -1
        var j = nums.size
        var mid = 0
        while((i+1) < j){
            mid = (i+j).ushr(1)
            if(nums[mid] >= target) j = mid
            else i = mid
        }
        
        return j
    }
```
