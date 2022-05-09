# 543. Diameter of Binary Tree

### 2017-03-20

Given a binary tree, you need to compute the length of the diameter of the tree. The diameter of a binary tree is the length of the **longest**path between any two nodes in a tree. This path may or may not pass through the root.

**Example:**
Given a binary tree 

```
          1
         / \
        2   3
       / \     
      4   5    

```

Return **3**, which is the length of the path [4,2,1,3] or [5,2,1,3].

**Note:** The length of path between two nodes is represented by the number of edges between them.



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
    func diameterOfBinaryTree(_ root: TreeNode?) -> Int {
        var diameter = 0
        func maxValue(_ root: TreeNode?) -> Int {
            guard let n = root else { return 0 }
            let l = maxValue(n.left)
            let r = maxValue(n.right)
            diameter = max(diameter , l + r)
            return max(l, r) + 1
        }
        _ = maxValue(root)
        return diameter

    }
}
```

