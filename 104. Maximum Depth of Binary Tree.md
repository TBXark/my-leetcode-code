# 104. Maximum Depth of Binary Tree

### 2017-03-16

Given a binary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.



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
    func maxDepth(_ root: TreeNode?) -> Int {
        guard let r = root else { return 0 }
        var temp = [root]
        var deep = 0
        while temp.count != 0 {
            deep += 1
            for _ in 0..<temp.count {
                let n = temp.removeFirst()
                if let l = n?.left { temp.append(l) }
                if let r = n?.right { temp.append(r) }
            }
        }
        return deep
    }
}
```

