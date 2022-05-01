Question: [https://leetcode.com/problems/plus-one/](https://leetcode.com/problems/plus-one/)
```kotlin
    fun plusOne(digits: IntArray): IntArray {
        var carry = false
        for(i in digits.size -1 downTo 0){
            val total = digits[i] + 1
            if(total > 9){
                digits[i] = total % 10
                carry = true
            }else{
                digits[i] = total
                carry = false
                break;
            }
        }
        if(carry){
            val tempList = digits.toMutableList()
            tempList.add(0,1)
            return tempList.toIntArray()
        }
        return digits
    }
```
