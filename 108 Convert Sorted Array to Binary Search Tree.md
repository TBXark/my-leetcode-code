# 108. Convert Sorted Array to Binary Search Tree

### 2017-03-15

Given an array where elements are sorted in ascending order, convert it to a height balanced BST.



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
    func sortedArrayToBST(_ nums: [Int]) -> TreeNode? {
        func sortedArrayToBST(nums: [Int], star: Int, end: Int) -> TreeNode? {
            guard star < end else { return nil }
            let m = (star + end)/2
            let r = TreeNode(nums[m])
            r.left = sortedArrayToBST(nums: nums, star: star, end: m)
            r.right = sortedArrayToBST(nums: nums, star: m + 1, end: end)
            return r
        }
        return sortedArrayToBST(nums: nums, star: 0, end: nums.count)
    }
}
```

