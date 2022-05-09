# 48. Rotate Image

### 2017-02-16

You are given an *n* x *n* 2D matrix representing an image.

Rotate the image by 90 degrees (clockwise).

Follow up:
Could you do this in-place?



# Solution

```swift
class Solution {
    func rotate(_ matrix: inout [[Int]]) {
        var a = 0
        var b = matrix.count - 1
        while a < b {
            for i in 0..<(b-a){
                swap(&matrix[a][a+i], &matrix[a+i][b])
                swap(&matrix[a][a+i], &matrix[b][b-i])
                swap(&matrix[a][a+i], &matrix[b-i][a])
            }
            a += 1
            b -= 1
        }
    }
} 
```

