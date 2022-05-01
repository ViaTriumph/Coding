Question: [https://leetcode.com/problems/min-stack/submissions/](https://leetcode.com/problems/min-stack/submissions/)
```kotlin
class MinStack() {
    
    val mStack = ArrayDeque<Int>()
    val minStack = ArrayDeque<Int>()
    
    fun push(value: Int) {
        mStack.push(value)
        if(minStack.size == 0){
            minStack.push(value)
        }else if(minStack.peek() >= value){
            minStack.push(value)
        }
    }

    fun pop() {
        if(mStack.peek() == minStack.peek()){
            minStack.pop()
        }
        mStack.pop()
    }

    fun top(): Int {
        return mStack.peek()
    }

    fun getMin(): Int {
        return minStack.peek()
    }

}
```
