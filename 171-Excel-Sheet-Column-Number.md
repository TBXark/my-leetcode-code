# 171. Excel Sheet Column Number

### 2017-02-20



Related to question [Excel Sheet Column Title](https://leetcode.com/problems/excel-sheet-column-title/)

Given a column title as appear in an Excel sheet, return its corresponding column number.

For example:

```
    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
```



# Solution

```swift
class Solution {
    func titleToNumber(_ s: String) -> Int {
      return  s.unicodeScalars.map({Int($0.value) - 64})
               .reduce(0) { $0 * 26 + $1 }
    }
}
```

