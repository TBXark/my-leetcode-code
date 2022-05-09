# 98. Validate Binary Search Tree

### 2017-03-11

Given a binary tree, determine if it is a valid binary search tree (BST).

Assume a BST is defined as follows:

- The left subtree of a node contains only nodes with keys **less than** the node's key.
- The right subtree of a node contains only nodes with keys **greater than** the node's key.
- Both the left and right subtrees must also be binary search trees.

**Example 1:**

```
    2
   / \
  1   3

```

Binary tree 

```
[2,1,3]
```

, return true.

**Example 2:**

```
    1
   / \
  2   3

```

Binary tree 

```
[1,2,3]
```

, return false.



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
    func isValidBST(_ root: TreeNode?) -> Bool {
        func isValidBST(root: TreeNode?, min: Int, max: Int) -> Bool {
            guard let r = root else { return  true }
            if r.val >= max || r.val <= min  { return false }
            return isValidBST(root: r.left, min: min, max: r.val) &&
                isValidBST(root: r.right, min: r.val, max: max)
        }
        return isValidBST(root: root, min: Int.min, max: Int.max)

    }
}
```

