Question: [https://leetcode.com/problems/invert-binary-tree/](https://leetcode.com/problems/invert-binary-tree/)
```kotlin
    fun invertTree(root: TreeNode?): TreeNode? {
        if(root == null){
            return root
        }
        
        val queue = ArrayDeque<TreeNode>()
        val mirrorQueue = ArrayDeque<TreeNode>()
        queue.push(root)
        val head = TreeNode(-1)
        mirrorQueue.push(head)
        while(!queue.isEmpty()){
            val top = queue.removeLast()
            val mTop = mirrorQueue.removeLast()
            
            mTop.`val` = top.`val` 
            if(top.left != null){
                mTop.right = TreeNode(-1)
                queue.push(top.left)
                mirrorQueue.push(mTop.right)
            }
            
            if(top.right != null){
                mTop.left = TreeNode(-1)
                queue.push(top.right)
                mirrorQueue.push(mTop.left)
            }
            
        }
        return head
    }
```
