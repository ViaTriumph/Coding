Question: [https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)
```kotlin
fun twoSum(nums: IntArray, target: Int): IntArray {
        val tNums = mutableListOf<Pair<Int, Int>>()
        for(i in 0..nums.size-1){
            tNums.add(Pair(nums[i],i))
        }

        val sNums = tNums.sortedBy{it.first}

        var i = 0
        var j = sNums.size-1
        var sum = 0
        while(i < j){
            sum = sNums[i].first + sNums[j].first
            if(sum == target){
                return intArrayOf(sNums[i].second,sNums[j].second)
            }else if(sum < target){
                i++
            }else{
                j--
            }
        }

        return intArrayOf(0,0)
}
```
