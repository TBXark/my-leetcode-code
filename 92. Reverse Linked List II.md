# 92. Reverse Linked List II

### 2017-03-02

Reverse a linked list from position *m* to *n*. Do it in-place and in one-pass.

For example:
Given `1->2->3->4->5->NULL`, *m* = 2 and *n* = 4,

return `1->4->3->2->5->NULL`.

**Note:**
Given *m*, *n* satisfy the following condition:
1 ≤ *m* ≤ *n* ≤ length of list.



# Solution

```swift
public class ListNode {
  public var val: Int
  public var next: ListNode?
  public init(_ val: Int) {
     self.val = val
     self.next = nil
 }
}

class Solution {
    
    func reverseBetween(_ head: ListNode?, _ m: Int, _ n: Int) -> ListNode? {
        if m == 1 {
            var newH: ListNode? = nil
            var oldH: ListNode? = head
            var c = n
            while let o = oldH {
                let next = o.next
                oldH?.next = newH
                newH = oldH
                oldH = next
                c -= 1
                if c == 0 {
                    head?.next = oldH
                    break
                }
            }
            return newH
        } else {
            head?.next = reverseBetween(head?.next, m - 1, n - 1)
            return head
        }
    }
}

```





