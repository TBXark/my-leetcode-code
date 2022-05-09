# 342. Power of Four

### 2017-03-30

Given an integer (signed 32 bits), write a function to check whether it is a power of 4.

**Example:**
Given num = 16, return true. Given num = 5, return false.

**Follow up**: Could you solve it without loops/recursion?



# Solution

```swift
class Solution {
 	func isPowerOfX(x: Int, num: Int) -> Bool {
         guard num > 0, x > 0 else { return false }
         let n = log10(Double(num)) / log10(Double(x))
         return (ceil(n) - n).isZero
    }
    func isPowerOfFour(_ num: Int) -> Bool {
         return isPowerOfX(x: 4, num: num)
    }
}
```

