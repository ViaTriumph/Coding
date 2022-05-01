Question: [https://leetcode.com/problems/binary-search/](https://leetcode.com/problems/binary-search/)

Bonus upper_bound & lower_bound implementations

```kotlin
fun search(nums: IntArray, target: Int): Int {
        var i = 0
        var j = nums.size-1
        var mid = (j + i)/2
        
        while(i <= j){
            mid = i + (j - i)/2
            if(nums[mid] == target){
                return mid
            }else if(nums[mid] > target){
                j = mid - 1
            }else{
                i = mid + 1
            }
        }
    
        
        return -1
    }
    
    fun lower_bound(nums: IntArray, target: Int): Int{
        var i = -1
        var j = nums.size
        var mid = 0
        
        while(i+1 < j){
            mid = (i+j).ushr(1)
            if(nums[mid] >= target) j = mid
            else i = mid
        }
        
        return j
    }
    
    fun upper_bound(nums: IntArray, target: Int): Int{
        var i = -1
        var j = nums.size
        var mid = 0
        
        while(i+1 < j){
            mid = (i+j).ushr(1)
            if(nums[mid] <= target) i = mid
            else j = mid
        }
        
        return i+1
    }
```
