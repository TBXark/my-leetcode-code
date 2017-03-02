# 206. Reverse Linked List

### 2017-03-02

Reverse a singly linked list.



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
    func reverseList(_ head: ListNode?) -> ListNode? {
        var newH: ListNode? = nil
        var oldH: ListNode? = head
        while let o = oldH {
            let next = o.next
            oldH?.next = newH
            newH = oldH
            oldH = next
        }
        return newH
    }
}
```

