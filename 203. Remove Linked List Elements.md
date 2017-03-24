# 203. Remove Linked List Elements

### 2017-03-24

Remove all elements from a linked list of integers that have value **val**.

**Example**
**\*Given:*** 1 --> 2 --> 6 --> 3 --> 4 --> 5 --> 6, **val** = 6
**\*Return:*** 1 --> 2 --> 3 --> 4 --> 5





# Solution

```swift
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     public var val: Int
 *     public var next: ListNode?
 *     public init(_ val: Int) {
 *         self.val = val
 *         self.next = nil
 *     }
 * }
 */
class Solution {
    func removeElements(_ head: ListNode?, _ val: Int) -> ListNode? {
        var newHead: ListNode? = nil
        var newTail: ListNode? = nil
        var current = head
        while let c = current {
            if c.val == val {
                current = c.next
            } else {
               if newTail == nil { 
                newHead = c
                newTail = c
               } else {
                   newTail?.next = c
                   newTail = c
               }
               current = c.next
               newTail?.next = nil
            }
            
        }
        return newHead
    }
}
```

