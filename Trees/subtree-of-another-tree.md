Question: [https://leetcode.com/problems/subtree-of-another-tree/](https://leetcode.com/problems/subtree-of-another-tree/)
```kotlin
    fun isSubtree(root: TreeNode?, subRoot: TreeNode?): Boolean {
        if(root == null && subRoot == null){
            return true
        }
        return dfs(root, subRoot)
    }
    
    fun dfs(node: TreeNode?, subRoot: TreeNode?): Boolean{
        if(node == null){
            return false
        }else if(node?.`val` == subRoot?.`val`){
            if(checkIfSameTree(node, subRoot)){
                return true
            }
        }
        return dfs(node?.left, subRoot) || dfs(node?.right, subRoot)

    }
    
    fun checkIfSameTree(node1: TreeNode?, node2: TreeNode?): Boolean{
        if(node1 == null && node2 == null){
            return true
        }else if(node1 != null && node2 != null && node1.`val` == node2.`val`){
            return checkIfSameTree(node1.left, node2.left) 
            && checkIfSameTree(node1.right, node2.right)
        }else{
            return false
        }
    }
```
