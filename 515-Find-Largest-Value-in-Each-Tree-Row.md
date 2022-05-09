# 515. Find Largest Value in Each Tree Row

### 2017-03-19

You need to find the largest value in each row of a binary tree.

**Example:**

```
Input: 

          1
         / \
        3   2
       / \   \  
      5   3   9 

Output: [1, 3, 9]
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
    func largestValues(_ root: TreeNode?) -> [Int] {
        guard let r = root else { return [] }
        var maxArr = [Int]()
        var layer = [r]
        while layer.count > 0 {
            var m = layer[0].val
            for i in 0..<layer.count {
                let n = layer.removeFirst()
                m = max(n.val, m)
                if let l = n.left { layer.append(l) }
                if let r = n.right { layer.append(r) }
            }
            maxArr.append(m)
        }
        return maxArr
    }
}
```

