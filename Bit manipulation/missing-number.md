Question: [https://leetcode.com/problems/missing-number/](https://leetcode.com/problems/missing-number/)
```kotlin
    fun missingNumber(nums: IntArray): Int {
        val fib = fibNum(nums.size)
        var count = 0
        for(i in 0..nums.size-1){
            count += nums[i]
        }
        return fib - count
    }
    
    fun fibNum(num: Int): Int{
        var count = 0
        for(i in 1..num){
            count += i
        }
        return count
    }
```
