# 7. Reverse Integer

### 2017-03-08

Reverse digits of an integer.

**Example1:** x = 123, return 321
**Example2:** x = -123, return -321

[click to show spoilers.](https://leetcode.com/problems/reverse-integer/?tab=Description#)

**Have you thought about this?**Here are some good questions to ask before coding. Bonus points for you if you have already thought through this!If the integer's last digit is 0, what should the output be? ie, cases such as 10, 100.Did you notice that the reversed integer might overflow? Assume the input is a 32-bit integer, then the reverse of 1000000003 overflows. How should you handle such cases?For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

**Note:**
The input is assumed to be a 32-bit signed integer. Your function should **return 0 when the reversed integer overflows**.



# Solution

```swift
class Solution {
    func reverse(_ x: Int) -> Int {
        var c = abs(x) 
        var r = 0
        let max = Int(Int32.max)
        while c != 0 {
            r = r * 10 + c % 10
            c = c / 10
            if r > max { return 0 }
        }
        return r * (x < 0 ? -1 : 1)
    }
}	
```

