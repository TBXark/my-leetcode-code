# 404. Sum of Left Leaves

### 2017-03-27

Find the sum of all left leaves in a given binary tree.

**Example:**

```
    3
   / \
  9  20
    /  \
   15   7

There are two left leaves in the binary tree, with values 9 and 15 respectively. Return 24.
```



# Solution

```swift
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     public var val: Int
 *     public var left: TreeNode?
 *     public var right: TreeNode?
 *     public init(_ val: Int) {
 *         self.val = val
 *         self.left = nil
 *         self.right = nil
 *     }
 * }
 */
class Solution {
    func sumOfLeftLeaves(_ root: TreeNode?) -> Int {
        guard let n = root else { return 0 }
        var layer = [n]
        var count = 0
        while layer.count > 0 {
            for i in 0..<layer.count {
                let node = layer.removeFirst()
                if let l = node.left {
                    if l.left == nil && l.right == nil {
                        count += l.val
                    }
                    layer.append(l)
                }
                if let r = node.right {
                    layer.append(r)
                }
            }
        }
        return count
    }
}
```

