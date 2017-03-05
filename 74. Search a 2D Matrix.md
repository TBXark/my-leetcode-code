# 74. Search a 2D Matrix

### 2017-03-05

Write an efficient algorithm that searches for a value in an *m* x *n* matrix. This matrix has the following properties:

- Integers in each row are sorted from left to right.
- The first integer of each row is greater than the last integer of the previous row.

For example,

Consider the following matrix:

```
[
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
]

```

Given **target** = `3`, return `true`.



# Solution

```swift
class Solution {
    func searchMatrix(_ matrix: [[Int]], _ target: Int) -> Bool {
        guard !matrix.isEmpty, !matrix[0].isEmpty else { return false }
        for y in 0..<matrix.count {
            for x in 0..<matrix[y].count {
                let v = matrix[y][x]
                if v == target {
                    return true
                } else if v > target {
                    return false
                }
            }
        }
        return false

    }
}
```

