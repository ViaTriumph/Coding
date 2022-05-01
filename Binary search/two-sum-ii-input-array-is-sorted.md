Question: [https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)
```kotlin
    fun twoSum(numbers: IntArray, target: Int): IntArray {
        
        var i = 0
        var j = numbers.size-1
        var sum = 0
        while(i < j){
            sum = numbers[i] + numbers[j]
            if(sum == target){
                return intArrayOf(i+1, j+1)   
            }else if(target > sum){
                i++
            }else{
                j--
            }
        }
        
        return intArrayOf()
    }
```
