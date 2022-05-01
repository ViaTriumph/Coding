Question: [https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)
```kotlin
    fun lowestCommonAncestor(root: TreeNode?, p: TreeNode?, q: TreeNode?): TreeNode? {
        var pList = mutableListOf<TreeNode>()
        var qList = mutableListOf<TreeNode>()
        
        var curr = root
        
        while(curr != null){
            pList.add(curr)
            if(p!= null && curr.`val` == p.`val`){
                break
            }else if(p!= null && curr.`val` > p.`val`){
                curr = curr.left
            }else{
                curr = curr.right
            }
        }
        curr = root
        while(curr != null){
            qList.add(curr)
            if(q != null && curr.`val` == q.`val`){
                break
            }else if(q != null && curr.`val` > q.`val`){
                curr = curr.left
            }else{
                curr = curr.right
            }
        }
        
        var i = 0
        var j = 0
        var lca: TreeNode? = null
        while(i < pList.size && j < qList.size){
            println("${pList[i].`val`}, ${qList[j].`val`}")
            if(pList[i].`val` != qList[j].`val`){
                break
            }else{
                lca = pList[i]
                i++
                j++
            }
        }
        
        return lca
    }
```
