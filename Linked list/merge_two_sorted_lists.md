Question: [https://leetcode.com/problems/merge-two-sorted-lists/](https://leetcode.com/problems/merge-two-sorted-lists/)
```kotlin
fun mergeTwoLists(list1: ListNode?, list2: ListNode?): ListNode? {
    var p1 = list1
    var p2 = list2
    var head = ListNode(-1)
    var curr = head

    while(p1 != null && p2 != null){
        if(p1.`val` == p2.`val`){
            curr.next = p1
            curr = curr.next
            p1 = p1.next

            curr.next = p2
            curr = curr.next
            p2 = p2.next
        }else if(p1.`val` < p2.`val`){
            curr.next = p1
            curr= curr.next
            p1 = p1.next
        }else{
            curr.next = p2
            curr = curr.next
            p2 = p2.next
        }
    }

    while(p1 != null){
        curr.next = p1
        curr = curr.next
        p1 = p1.next
    }

    while(p2 != null){
        curr.next = p2
        curr = curr.next
        p2 = p2.next
    }

    return head.next
}
```
