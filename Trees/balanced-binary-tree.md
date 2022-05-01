Question: [https://leetcode.com/problems/balanced-binary-tree/](https://leetcode.com/problems/balanced-binary-tree/)
```kotlin
    fun isBalanced(root: TreeNode?): Boolean {
        val res = dfs(root)
        return res.second
    }
    
    fun dfs(root: TreeNode?): Pair<Int, Boolean>{
        if(root == null){
            return Pair(0,  true)
        }
        
        var left = Pair(0, true)
        var right = Pair(0, true)
        if(root.left != null){
            left = dfs(root.left)
        }
        if(root.right != null){
            right = dfs(root.right)
        }

        
        return Pair( 1 + maxOf(left.first, right.first), 
                    left.second && right.second && Math.abs(left.first-right.first) <= 1)
    }
```
