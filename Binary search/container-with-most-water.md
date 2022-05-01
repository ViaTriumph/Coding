Question: [https://leetcode.com/problems/container-with-most-water/](https://leetcode.com/problems/container-with-most-water/)
```kotlin
    fun maxArea(height: IntArray): Int {
        var i = 0
        var j = height.size-1
        var maxWater = 0
        var ans = 0
        while(i < j){
            if(height[i] <= height[j]){
                ans = height[i]*(j-i)
                i++
            }else{
                ans = height[j]*(j-i)
                j--
            }
            maxWater = maxOf(maxWater, ans)
        }
        return maxWater
    }
```
