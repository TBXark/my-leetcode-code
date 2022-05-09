# 21. Merge Two Sorted Lists

### 2017-03-03

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.



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
extension ListNode {
    func setNext(n: ListNode?) -> ListNode {
        next = n
        return self
    }
}

class Solution {
    func mergeTwoLists(_ l1: ListNode?, _ l2: ListNode?) -> ListNode? {
        guard let n1 = l1, let n2 = l2 else { return l1 ?? l2 }
        return n1.val < n2.val ? n1.setNext(n: mergeTwoLists(n1.next, n2)) : n2.setNext(n: mergeTwoLists(n2.next, n1))
    }
}
```

