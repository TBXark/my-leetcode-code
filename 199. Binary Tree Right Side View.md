# 199. Binary Tree Right Side View

### 2017-02-19

Given a binary tree, imagine yourself standing on the *right* side of it, return the values of the nodes you can see ordered from top to bottom.

For example:
Given the following binary tree,

```
   1            <---
 /   \
2     3         <---
 \     \
  5     4       <---

```

You should return `[1, 3, 4]`.



# Solution



```swift
public class TreeNode {
  public var val: Int
  public var left: TreeNode?
  public var right: TreeNode?
  public init(_ val: Int) {
    self.val = val
    self.left = nil
    self.right = nil
    }
}


class Solution {
    
    func rightSideView(_ root: TreeNode?) -> [Int] {
        guard let r = root else { return [] }
        var nodes = [r]
        var res = [Int]()
        while !nodes.isEmpty {
            for i in 0..<nodes.count {
                let top = nodes.removeFirst()
                if i == 0 { res.append(top.val) }
                if let l = top.right { nodes.append(l)}
                if let r = top.left { nodes.append(r) }
            }
        }
        return res
    }
}

```

