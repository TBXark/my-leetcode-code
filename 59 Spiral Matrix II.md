# 59. Spiral Matrix II

### 2016-02-23

Given an integer *n*, generate a square matrix filled with elements from 1 to *n*2 in spiral order.

For example,
Given *n* = `3`,

You should return the following matrix:

```
[
 [ 1, 2, 3 ],
 [ 8, 9, 4 ],
 [ 7, 6, 5 ]
]
```



# Solution

```swift
class Solution {
//    func printN(_ n: [[Int]]) {
//        n.forEach{ print("\($0)")}
//        print("\n")
//    }
    func generateMatrix(_ n: Int) -> [[Int]] {
        var array = Array.init(repeating: Array.init(repeating: 0, count: n), count: n)
        var length = n
        var changeFlag = true
        var x = 0
        var y = 0
        var dx = 1
        var dy = 0
        var v  = 1
        while length > 0 {
            for _ in 0..<length {
                array[y][x] = v
                x += dx
                y += dy
                v += 1
//                printN(array)
            }
            x -= dx
            y -= dy
            switch (dx, dy) {
            case (1, 0):
                dx = 0
                dy = 1
            case (0, 1):
                dx = -1
                dy = 0
            case (-1, 0):
                dx = 0
                dy = -1
            case (0, -1):
                dx = 1
                dy = 0
            default:
                break
            }
            x += dx
            y += dy
            if changeFlag {
                length -= 1
                changeFlag = false
            } else {
                changeFlag = true
            }
        }
        return array
    }
}
```

