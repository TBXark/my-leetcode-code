# 83. Remove Duplicates from Sorted List

### 2017-04-06

Given a sorted linked list, delete all duplicates such that each element appear only *once*.

For example,
Given `1->1->2`, return `1->2`.
Given `1->1->2->3->3`, return `1->2->3`.



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
    func deleteDuplicates(_ head: ListNode?) -> ListNode? {
        guard var current = head else { return head }
        while let next = current.next {
            if current.val == next.val {
                current.next = next.next
            } else {
                current = next
            }
        }
        return head
    }
}
```

