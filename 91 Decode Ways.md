# 91. Decode Ways

### 2020-07-31

A message containing letters from A-Z is being encoded to numbers using the following mapping:

```
'A' -> 1
'B' -> 2
...
'Z' -> 26
```
Given a non-empty string containing only digits, determine the total number of ways to decode it.

Example 1:
```
Input: "12"
Output: 2
Explanation: It could be decoded as "AB" (1 2) or "L" (12).
```
Example 2:
```
Input: "226"
Output: 3
Explanation: It could be decoded as "BZ" (2 26), "VF" (22 6), or "BBF" (2 2 6).
```

# Solution

```swift
class Solution {
    private var cache = [Int]()
    private func numDecodingsForSubString(start: Int, end: Int, c: [Int8]) -> Int {
        let index = start * 2 + (end - start) - 1
        if cache[index] >= 0  {
            return cache[index]
        }
        guard end <= c.count, c[start] != 0, isLetters(c[start..<end]) else {
            cache[index] = 0
            return 0
        }
        if end == c.count {
            cache[index] = 1
            return 1
        }
        let count = numDecodingsForSubString(start: end, end: end + 1, c: c) + numDecodingsForSubString(start: end, end: end + 2, c: c)
        cache[index] = count
        return count
    }
    
    private func isLetters(_ array: ArraySlice<Int8>) -> Bool {
        var i = Int8(0)
        for c in array {
            i = i * 10 + c
        }
        return i >= 1 && i <= 26
    }

    func numDecodings(_ s: String) -> Int {
        var c = s.utf8CString.map({  $0 - 48 })
        c.removeLast()
        cache = [Int].init(repeating: -1, count: c.count * 2)
        return numDecodingsForSubString(start: 0, end: 1, c: c) + numDecodingsForSubString(start: 0, end: 2, c: c)
    }
}


```
