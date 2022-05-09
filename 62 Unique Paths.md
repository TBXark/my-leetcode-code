# 62. Unique Paths

### 2020-07-31

A robot is located at the top-left corner of a *m* x *n* grid (marked 'Start' in the diagram below).

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked 'Finish' in the diagram below).

How many possible unique paths are there?

![img](https://assets.leetcode.com/uploads/2018/10/22/robot_maze.png)

Above is a 7 x 3 grid. How many possible unique paths are there?

 

**Example 1:**

```
Input: m = 3, n = 2
Output: 3
Explanation:
From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:
1. Right -> Right -> Down
2. Right -> Down -> Right
3. Down -> Right -> Right
```

**Example 2:**

```
Input: m = 7, n = 3
Output: 28
```

 

**Constraints:**

- `1 <= m, n <= 100`
- It's guaranteed that the answer will be less than or equal to `2 * 10 ^ 9`.


# Solution

```swift
class Solution {
    func uniquePaths(_ m: Int, _ n: Int) -> Int {
        var cache = [[Int]].init(repeating: [Int].init(repeating: 0, count: n), count: m)
        for y in 1...m {
            for x in 1...n {
                if x == 1 || y == 1 {
                    cache[y - 1][x - 1] = 1
                } else {
                    cache[y - 1][x - 1] = cache[y - 2][x - 1] + cache[y - 1][x - 2]
                }
            }
        }
        return cache[m - 1][n - 1]
    }
}

```

