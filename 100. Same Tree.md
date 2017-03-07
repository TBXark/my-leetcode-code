# 100. Same Tree

### 2017-03-07

Given two binary trees, write a function to check if they are equal or not.

Two binary trees are considered equal if they are structurally identical and the nodes have the same value.



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
    func isSameTree(_ p: TreeNode?, _ q: TreeNode?) -> Bool {
        guard let pp = p, let qq = q else { return p == nil && q == nil   }
        guard pp.val == qq.val else { return false }
        return isSameTree(pp.left, qq.left)  &&  isSameTree(pp.right, qq.right)
    }
}
```

