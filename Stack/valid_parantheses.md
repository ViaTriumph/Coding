Question: [https://leetcode.com/problems/valid-parentheses/](https://leetcode.com/problems/valid-parentheses/)
```kotlin
fun isValid(s: String): Boolean {
        val stack = ArrayDeque<Char>()
        var isValid = true
        for(c in s){
            if(c == '(' || c == '{' || c == '['){
                stack.push(c)
            }else if(c == ')' && stack.peek() == '('){
                stack.pop()
            }else if(c == '}' && stack.peek() == '{'){
                stack.pop()
            }else if(c == ']' && stack.peek() == '['){
                stack.pop()
            }else{
                isValid = false
                break
            }
        }
        if(isValid == true && stack.size != 0){
            isValid = false
        }
        
        return isValid
    }
```
