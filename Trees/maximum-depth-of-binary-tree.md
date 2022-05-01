Question: [https://leetcode.com/problems/maximum-depth-of-binary-tree/](https://leetcode.com/problems/maximum-depth-of-binary-tree/)
```kotlin
    fun maxDepth(root: TreeNode?): Int {
        val queue = ArrayDeque<Pair<TreeNode, Int>>()
        if(root == null){
            return 0
        }
        var currHeight = 1
        queue.add(Pair(root, currHeight))
        while(!queue.isEmpty()){
            val topEl = queue.removeFirst()
            val node = topEl.first
            currHeight = topEl.second
            if(node.left != null){
                queue.add(Pair(node.left,currHeight + 1))
            }
            if(node.right != null){
                queue.add(Pair(node.right,currHeight + 1))
            }
        }
        return currHeight
    }
```
