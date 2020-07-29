# 51. N-Queens

### 2020-07-29

The *n*-queens puzzle is the problem of placing *n* queens on an *n*×*n* chessboard such that no two queens attack each other.

![img](https://assets.leetcode.com/uploads/2018/10/12/8-queens.png)


# Solution

```swift
 
class Solution {
      
   private func checkLine(y: Int, n: Int, col: inout [Bool], row: inout [Int], d1: inout [Bool], d2: inout [Bool], res: inout [[String]]) {
        if y == n {
            var temp = [String]()
            for i in 0..<n {
                var line = Array<Character>.init(repeating: ".", count: n)
                line[row[i]] = "Q"
                temp.append(String(line))
            }
            res.append(temp)
        } else {
            for x in 0..<n {
                if !col[x], !d1[x + y], !d2[x - y + (n - 1)] {
                    col[x] = true
                    d1[x+y] = true
                    d2[x - y + (n - 1)] = true
                    row[y] = x
                    checkLine(y: y + 1, n: n, col: &col, row: &row, d1: &d1, d2: &d2, res: &res)
                    col[x] = false
                    d1[x+y] = false
                    d2[x - y + (n - 1)] = false
                }
            }
        }
    }
    
    func solveNQueens(_ n: Int) -> [[String]] {
        var res = [[String]]()
        guard n > 0 else {
            return res
        }
        var col = [Bool].init(repeating: false, count: n)
        var row = [Int].init(repeating: 0, count: n)
        var d1 = [Bool].init(repeating: false, count: (2 * n ) - 1)
        var d2 = [Bool].init(repeating: false, count: (2 * n ) - 1)
        checkLine(y: 0, n: n, col: &col, row: &row, d1: &d1, d2: &d2, res: &res)
        return res
    }
}

```
