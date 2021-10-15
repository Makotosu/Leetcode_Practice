### 19.Remove Nth Node From End of List
Given the head of a linked list, remove the nth node from the end of the list and return its head.

```
Example
Input: head = [1,2,3,4,5], n = 2
Output: [1,2,3,5]
```
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        dummy = ListNode(0,head)
        left = dummy
        right = head
        
        while n > 0 and right:
            right = right.next
            n -=1
            
        while right:
            left = left.next
            right = right.next
        #delete
        left.next = left.next.next
        return dummy.next
