# 37. Sudoku Solver

### 2020-07-29

Write a program to solve a Sudoku puzzle by filling the empty cells.

A sudoku solution must satisfy **all of the following rules**:

1. Each of the digits `1-9` must occur exactly once in each row.
2. Each of the digits `1-9` must occur exactly once in each column.
3. Each of the the digits `1-9` must occur exactly once in each of the 9 `3x3` sub-boxes of the grid.

Empty cells are indicated by the character `'.'`.

![img](https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/250px-Sudoku-by-L2G-20050714.svg.png)
A sudoku puzzle...

![img](https://upload.wikimedia.org/wikipedia/commons/thumb/3/31/Sudoku-by-L2G-20050714_solution.svg/250px-Sudoku-by-L2G-20050714_solution.svg.png)
...and its solution numbers marked in red.

**Note:**

- The given board contain only digits `1-9` and the character `'.'`.
- You may assume that the given Sudoku puzzle will have a single unique solution.
- The given board size is always `9x9`.


# Solution

顺序遍历
```swift

class Solution {
    static let num: [Character] = ["1", "2", "3", "4", "5", "6", "7", "8", "9"]

    func solveSudoku(_ board: inout [[Character]]) {
        var clo = [Set<Character>].init(repeating: Set<Character>(), count: 9)
        var row = [Set<Character>].init(repeating: Set<Character>(), count: 9)
        var block = [Set<Character>].init(repeating: Set<Character>(), count: 9)
        for y in 0..<9 {
            for x in 0..<9 {
                let c = board[y][x]
                guard c != "." else {
                    continue
                }
                clo[y].insert(c)
                row[x].insert(c)
                block[x/3 + (y/3) * 3].insert(c)
            }
        }
        _ = fillGrid(index: 0, board: &board, clo: &clo, row: &row, block: &block)
    }
    
    
    func fillGrid(index: Int,
                  board: inout [[Character]],
                  clo: inout [Set<Character>],
                  row: inout [Set<Character>],
                  block: inout [Set<Character>]) -> Bool {
        guard index < 81 else {
            return true
        }
        var i = index
        var x = i % 9
        var y = i / 9
        while board[y][x] != "." {
            i += 1
            guard i < 81  else {
               return true
            }
            x = i % 9
            y = i / 9
        }
        
        for c in Solution.num {
            if !clo[y].contains(c), !row[x].contains(c), !block[x/3 + (y/3) * 3].contains(c) {
                board[y][x] = c
                clo[y].insert(c)
                row[x].insert(c)
                block[x/3 + (y/3) * 3].insert(c)
                if fillGrid(index: i + 1, board: &board, clo: &clo, row: &row, block: &block) {
                    return true
                } else {
                    clo[y].remove(c)
                    row[x].remove(c)
                    block[x/3 + (y/3) * 3].remove(c)
                    board[y][x] = "."
                }
            }
        }
        return false
    }
    
}


```


按照权重遍历
```swift

class Solution {
   
    static let num: [Character] = ["1", "2", "3", "4", "5", "6", "7", "8", "9"]

    func solveSudoku(_ board: inout [[Character]]) {
        var clo = [Set<Character>].init(repeating: Set<Character>(), count: 9)
        var row = [Set<Character>].init(repeating: Set<Character>(), count: 9)
        var block = [Set<Character>].init(repeating: Set<Character>(), count: 9)
        var points = [(p: (x: Int, y: Int), c: Int)]()
        for y in 0..<9 {
            for x in 0..<9 {
                let c = board[y][x]
                guard c != "." else {
                    points.append((p: (x: x, y: y), c: 0))
                    continue
                }
                clo[y].insert(c)
                row[x].insert(c)
                block[x/3 + (y/3) * 3].insert(c)
            }
        }
        for i in 0..<points.count {
            let (x, y) = points[i].p
            var set = clo[y] 
            for c in row[x] {
                set.insert(c)
            }
            for c in block[x/3 + (y/3) * 3] {
                set.insert(c)
            }
            points[i].c = set.count
        }
        _ = fillGrid(index: 0,
                     point: points.sorted(by: { $0.c > $1.c }).map({ $0.p }),
                     board: &board,
                     clo: &clo,
                     row: &row,
                     block: &block)
    }
    
    
    func fillGrid(index: Int,
                  point: [(x: Int, y: Int)],
                  board: inout [[Character]],
                  clo: inout [Set<Character>],
                  row: inout [Set<Character>],
                  block: inout [Set<Character>]) -> Bool {
        if index == point.count  {
            return true
        }
        let (x, y) = point[index]
        for c in Solution.num {
            if !clo[y].contains(c), !row[x].contains(c), !block[x/3 + (y/3) * 3].contains(c) {
                board[y][x] = c
                clo[y].insert(c)
                row[x].insert(c)
                block[x/3 + (y/3) * 3].insert(c)
                if fillGrid(index: index + 1, point: point, board: &board, clo: &clo, row: &row, block: &block) {
                    return true
                } else {
                    clo[y].remove(c)
                    row[x].remove(c)
                    block[x/3 + (y/3) * 3].remove(c)
                    board[y][x] = "."
                }
            }
        }
        return false
    }
}


```

对于测试数组 
```
[["5","3",".",".","7",".",".",".","."],
["6",".",".","1","9","5",".",".","."],
[".","9","8",".",".",".",".","6","."],
["8",".",".",".","6",".",".",".","3"],
["4",".",".","8",".","3",".",".","1"],
["7",".",".",".","2",".",".",".","6"],
[".","6",".",".",".",".","2","8","."],
[".",".",".","4","1","9",".",".","5"],
[".",".",".",".","8",".",".","7","9"]]
```
顺序遍历调用`fillGrid` 4209次，按权重遍历调用`fillGrid` 103次




对权重遍历就行优化，提前得到每个空位有可能的值进行遍历，由于对集合进行遍历顺序不确定，所以导致时间不稳定。最优时间可能在排名在100%
```
Runtime: 36 ms, faster than 100.00% of Swift online submissions for Sudoku Solver.
Memory Usage: 22.5 MB, less than 50.00% of Swift online submissions for Sudoku Solver.
```

```swift
class Solution {

    static let num: Set<Character> = ["1", "2", "3", "4", "5", "6", "7", "8", "9"]

    func solveSudoku(_ board: inout [[Character]]) {
        var clo = [Set<Character>].init(repeating: Set<Character>(), count: 9)
        var row = [Set<Character>].init(repeating: Set<Character>(), count: 9)
        var block = [Set<Character>].init(repeating: Set<Character>(), count: 9)
        var points = [(p: (x: Int, y: Int), c: Int)]()
        for y in 0..<9 {
            for x in 0..<9 {
                let c = board[y][x]
                guard c != "." else {
                    points.append((p: (x: x, y: y), c: 0))
                    continue
                }
                clo[y].insert(c)
                row[x].insert(c)
                block[x/3 + (y/3) * 3].insert(c)
            }
        }
        for i in 0..<points.count {
            let (x, y) = points[i].p
            points[i].c = clo[y].union(row[x]).union(block[x/3 + (y/3) * 3]).count
        }
        _ = fillGrid(index: 0,
                     point: points.sorted(by: {  $0.c > $1.c  }).map({ $0.p }),
                     board: &board,
                     clo: &clo,
                     row: &row,
                     block: &block)
    }


    func fillGrid(index: Int,
                  point: [(x: Int, y: Int)],
                  board: inout [[Character]],
                  clo: inout [Set<Character>],
                  row: inout [Set<Character>],
                  block: inout [Set<Character>]) -> Bool {
        if index == point.count  {
            return true
        }
        let (x, y) = point[index]
        for c in Solution.num.subtracting(clo[y].union(row[x]).union(block[x/3 + (y/3) * 3])) {
            board[y][x] = c
            clo[y].insert(c)
            row[x].insert(c)
            block[x/3 + (y/3) * 3].insert(c)
            if fillGrid(index: index + 1, point: point, board: &board, clo: &clo, row: &row, block: &block) {
                return true
            } else {
                clo[y].remove(c)
                row[x].remove(c)
                block[x/3 + (y/3) * 3].remove(c)
                board[y][x] = "."
            }
        }
        return false
    }
}

```
