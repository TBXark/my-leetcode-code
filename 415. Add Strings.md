# 415. Add Strings

### 2017-04-05

Given two non-negative integers `num1` and `num2` represented as string, return the sum of `num1` and `num2`.

**Note:**

1. The length of both `num1` and `num2` is < 5100.
2. Both `num1` and `num2` contains only digits `0-9`.
3. Both `num1` and `num2` does not contain any leading zero.
4. You **must not use any built-in BigInteger library** or **convert the inputs to integer** directly.



# Solution

```swift
class Solution {
    func addStrings(_ num1: String, _ num2: String) -> String {
        func toIntArray(string: String) -> [Int8] {
            guard var n = string.cString(using: String.Encoding.utf8) else { return [] }
            n = n.reversed()
            n.removeFirst()
            return n.map({ (v: Int8) -> Int8 in
                return v - 48
            })
        }
        
        let n1 = toIntArray(string: num1)
        let n2 = toIntArray(string: num2)
        let count = max(n1.count, n2.count)
        var n3 = [Int8](repeating: 0, count: count + 1)

        for i in 0..<count {
            let c = (i < n1.count ? n1[i] : 0) + (i < n2.count ? n2[i] : 0)
            n3[i] = n3[i] + c
            if n3[i] >= 10 {
                n3[i + 1] += n3[i] / 10
                n3[i] = n3[i] % 10
            }
        }
         if let n = n3.last, n == 0 {
            n3.removeLast()
        }
        
        if n3.count > 0 {
            return n3.reduce("", { "\($1)\($0)"})
        } else {
            return "0"
        }       
    }
}
```

