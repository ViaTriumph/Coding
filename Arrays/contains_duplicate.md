Question: [https://leetcode.com/problems/contains-duplicate/](https://leetcode.com/problems/contains-duplicate/)

```kotlin
fun containsDuplicate(nums: IntArray): Boolean {
        val isVisited = hashMapOf<Int, Boolean>()

        for(i in 0..nums.size-1){
            if(isVisited[nums[i]] == true){
                return true
            }
            isVisited[nums[i]] = true
        }

        return false
}
```
