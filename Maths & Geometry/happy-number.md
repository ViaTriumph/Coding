Question: [https://leetcode.com/problems/happy-number/](https://leetcode.com/problems/happy-number/)
```kotlin
    fun isHappy(n: Int): Boolean {
        var slow = calculateSquareSum(n)
        var fast = calculateSquareSum(n)
        fast = calculateSquareSum(fast)
        
        while(slow != fast){
            slow = calculateSquareSum(slow)
            fast = calculateSquareSum(fast)
            fast = calculateSquareSum(fast)
        }
        
        return if(slow == 1) true
        else false
    }
    
    fun calculateSquareSum(n: Int): Int{
        var sum = 0
        var num = n
        while(num > 0){
            sum += ((num%10)*(num%10))
            num /= 10
        }
        return sum
    }
```
