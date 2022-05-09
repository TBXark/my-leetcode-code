# 513. Find Bottom Left Tree Value

### 2017-03-17

Given a binary tree, find the leftmost value in the last row of the tree.

**Example 1:**

```
Input:

    2
   / \
  1   3

Output:
1

```

**Example 2: **

```
Input:

        1
       / \
      2   3
     /   / \
    4   5   6
       /
      7

Output:
7

```

**Note:** You may assume the tree (i.e., the given root node) is not **NULL**.



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
    func findBottomLeftValue(_ root: TreeNode?) -> Int {
        guard let r = root else { return 0 }
        var layer = [r]
        var lastLeft = r
        while layer.count > 0 {
            for i in 0..<layer.count {
                let n = layer.removeFirst()
                if let l = n.left { layer.append(l) }
                if let r = n.right { layer.append(r) }
            }            
            lastLeft = layer.first ?? lastLeft
        }
        return lastLeft.val
    }
}
```

