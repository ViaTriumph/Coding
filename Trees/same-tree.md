Question: [https://leetcode.com/problems/same-tree/](https://leetcode.com/problems/same-tree/)
```kotlin
    fun isSameTree(p: TreeNode?, q: TreeNode?): Boolean {
        val q1 = ArrayDeque<TreeNode>()
        val q2 = ArrayDeque<TreeNode>()
        if(p == null && q == null){
            return true
        }else if(p == null && q != null){
            return false
        }else if(p != null && q == null){
            return false
        }
        
        q1.add(p)
        q2.add(q)
        
        while(!q1.isEmpty() && !q2.isEmpty()){
            val top1 = q1.removeFirst()
            val top2 = q2.removeFirst()
        
            
            if(top1.`val` != top2.`val`){
                println(top1.`val` != top1.`val`)
                return false
            }
            
            if(top1.left != null && top2.left != null){
                q1.add(top1.left)
                q2.add(top2.left)
            }else if(top1.left == null && top2.left == null){
                
            }else{
                return false
            }
            
            if(top1.right != null && top2.right != null){
                q1.add(top1.right)
                q2.add(top2.right)
            }else if(top1.right == null && top2.right == null){
                
            }else{
                return false
            }
        }
        
        return q1.isEmpty() && q2.isEmpty()
    }
```
