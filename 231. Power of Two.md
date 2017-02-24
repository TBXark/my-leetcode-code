# 231. Power of Two

Given an integer, write a function to determine if it is a power of two.



# Solution

```swift
class Solution {
    func isPowerOfTwo(_ n: Int) -> Bool {
         return n > 0 ? (n == 1 ? true : (n % 2 == 0) && isPowerOfTwo(n / 2)) : false
    }
}
```

