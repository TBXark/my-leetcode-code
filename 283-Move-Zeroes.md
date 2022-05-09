# 283. Move Zeroes



Given an array `nums`, write a function to move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.

For example, given `nums = [0, 1, 0, 3, 12]`, after calling your function, `nums` should be `[1, 3, 12, 0, 0]`.

**Note**:

1. You must do this **in-place** without making a copy of the array.
2. Minimize the total number of operations.



# Solution



```swift
class Solution {
     func moveZeroes(_ nums: inout [Int]) {
        var cur = 0
        for i in 0..<nums.count {
            if (nums[i] != 0) {
                nums[cur] = nums[i]
                cur += 1
            }
        }
        for i in cur..<nums.count {
            nums[i] = 0;
        }
        
    }
}
```

