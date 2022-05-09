# 344. Reverse String
### 2017-02-25
Write a function that takes a string as input and returns the string reversed.

**Example:**
Given s = "hello", return "olleh".



# Solution

```swift
class Solution {
    func reverseString(_ s: String) -> String {
          return  s.characters.reversed().reduce("", { $0+"\($1)"})
    }
}
```

