# 257. Binary Tree Paths

### 2017-03-21

Given a binary tree, return all root-to-leaf paths.

For example, given the following binary tree:

```
   1
 /   \
2     3
 \
  5

```

All root-to-leaf paths are:

```
["1->2->5", "1->3"]
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
    func binaryTreePaths(_ root: TreeNode?) -> [String] {
        guard let n = root else { return [] }
        var path = [String]()
        if n.left == nil && n.right == nil { return ["\(n.val)"]}
        for p in binaryTreePaths(n.left) {
            path.append("\(n.val)->\(p)")
        }
        for p in binaryTreePaths(n.right) {
            path.append("\(n.val)->\(p)")
        }
        return path
    }
}
```

