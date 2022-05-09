# 100. Perfect Squares

### 2020-07-30

Given a positive integer n, find the least number of perfect square numbers (for example, `1, 4, 9, 16, ...`) which sum to n.

Example 1:
```
Input: n = 12
Output: 3 
Explanation: 12 = 4 + 4 + 4.
```

Example 2:
```
Input: n = 13
Output: 2
Explanation: 13 = 4 + 9.
```

# Solution

```swift
class Solution {
    
    var cache = [Int: Int]()
    var perfectSquare = [Int]()
    
    func findSum(count: Int, num: Int) -> Bool {
        switch count {
        case 0:
            return false
        case 1:
            guard let c = cache[num] else {
                return false
            }
            return c == 1
        default:
            if cache[num] != nil {
                return true
            }
            for sn in perfectSquare {
                if findSum(count: count - 1, num: num - sn) {
                    cache[num] = count
                    return true
                }
            }
            return false
        }
    }
    
    func numSquares(_ n: Int) -> Int {
        guard n > 0 else {
            return 0
        }
        for i in 1...n {
            let sq = i * i
            guard sq <= n else {
                break
            }
            cache[sq] = 1
            perfectSquare.append(sq)
        }
        for i in 1...n {
            if findSum(count: i, num: n) {
                return i
            }
        }
        return n
    }
}
```
