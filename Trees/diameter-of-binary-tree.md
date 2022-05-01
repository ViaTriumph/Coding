Question: [https://leetcode.com/problems/diameter-of-binary-tree/](https://leetcode.com/problems/diameter-of-binary-tree/)
```kotlin
    var maxV = 0
    fun diameterOfBinaryTree(root: TreeNode?): Int {
        maxV = 0
        dfs(root)
        return maxV - 1
    }
    
    fun dfs(root: TreeNode?): Int{
        if(root == null){
            return 0
        }
        
        val left = dfs(root.left)
        val right = dfs(root.right)
        
        maxV = maxOf(maxV , left + right + 1)
        return 1 + maxOf(left, right)
    }
```
