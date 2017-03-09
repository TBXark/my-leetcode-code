# 112. Path Sum

### 2017-03-09

Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

For example:

Given the below binary tree and 

```
sum = 22
```

,

```
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \      \
        7    2      1

```

return true, as there exist a root-to-leaf path `5->4->11->2` which sum is 22.



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
    func hasPathSum(_ root: TreeNode?, _ sum: Int) -> Bool {
        guard let node = root else { return false }
        if let l = node.left, let r = node.right {
            return hasPathSum(l, sum - node.val) || hasPathSum(r, sum - node.val)
        } else if let r = node.left ?? node.right {
            return hasPathSum(r, sum - node.val )
        } else {
            return sum == node.val
        }

    }
}
```

