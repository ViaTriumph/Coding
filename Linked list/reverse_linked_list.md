Question: [https://leetcode.com/problems/reverse-linked-list/](https://leetcode.com/problems/reverse-linked-list/)
```kotlin
fun reverseList(head: ListNode?): ListNode? {
    if(head == null){
        return null
    }
    var bNode = ListNode(head.`val`)
    var cNode = head.next

    while(cNode != null){
        val newNode = ListNode(cNode.`val`)
        newNode.next = bNode
        bNode = newNode
        cNode = cNode.next
    }

    return bNode
}
```
