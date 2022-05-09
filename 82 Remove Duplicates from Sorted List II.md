# 82. Remove Duplicates from Sorted List II

### 2017-03-10

Given a sorted linked list, delete all nodes that have duplicate numbers, leaving only *distinct* numbers from the original list.

For example,
Given `1->2->3->3->4->4->5`, return `1->2->5`.
Given `1->1->1->2->3`, return `2->3`.



# Solution*

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
    func deleteDuplicates(_ head: ListNode?) -> ListNode? {
        guard  head != nil else { return nil }
        let temp: ListNode = ListNode.init(-1)
        temp.next = head
        var pre: ListNode? = temp
        var cur: ListNode? = head
        while  cur != nil {
            while let nv = cur?.next?.val, let cv = cur?.val, nv == cv {
                cur = cur?.next
            }
            if let pn = pre?.next, let c = cur, pn === c {
                pre = pre?.next
            } else {
                pre?.next = cur?.next
            }
            cur = cur?.next
        }
        
        return temp.next

    }
}
```







