Question: [https://leetcode.com/problems/target-sum/](https://leetcode.com/problems/target-sum/)
```kotlin
    fun findTargetSumWays(nums: IntArray, target: Int): Int {
        var count = 0
        nums.forEach{num -> 
            count += num 
        }
        
        var arr = Array(nums.size){IntArray(2*count+1){0}}
        
        for(i in 0..nums.size-1){
            for(j in 0..2*count){
                if(i == 0){
                    if(j - count - nums[i] == 0){
                        arr[i][j]++
                    }
                    if(j - count + nums[i] == 0){
                        arr[i][j]++
                    }
                }else if(j - nums[i] >= 0 
                        && j - nums[i] <= 2*count
                        && j + nums[i] >= 0
                        && j + nums[i] <= 2*count
                        && arr[i-1][j - nums[i]] != 0
                        && arr[i-1][j + nums[i]] != 0){
                    arr[i][j] = arr[i-1][j - nums[i]] + arr[i-1][j + nums[i]]
                }else if(j - nums[i] >= 0 
                        && j - nums[i] <= 2*count
                        && arr[i-1][j - nums[i]] != 0){
                    arr[i][j] = arr[i-1][j - nums[i]] 
                }else if(j + nums[i] >= 0
                        && j + nums[i] <= 2*count
                        && arr[i-1][j + nums[i]] != 0){
                    arr[i][j] = arr[i-1][j + nums[i]]
                }
            }
        }
        

        return if(target + count >= 0 && target + count <= 2*count) {
            arr[nums.size-1][target+count]
        }else 0
         
    }
```
