# 326. Power of Three

### 2017-03-29

Given an integer, write a function to determine if it is a power of three.

**Follow up:**
Could you do it without using any loop / recursion?



# Solution

```swift
class Solution {
    func isPowerOfThree(_ n: Int) -> Bool {
        guard n > 0 else { return false }
        let num = log10(Double(n)) / log10(3)
        return (ceil(num) - num).isZero
    }
}
```

