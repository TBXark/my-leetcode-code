# 557. Reverse Words in a String III

### 2017-04-09

Given a string, you need to reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.

**Example 1:**

```
Input: "Let's take LeetCode contest"
Output: "s'teL ekat edoCteeL tsetnoc"

```

**Note:** In the string, each word is separated by single space and there will not be any extra space in the string.



# Solution

```swift
class Solution {
    func reverseWords(_ s: String) -> String {
        return s.components(separatedBy: " ")
            .flatMap({ $0.characters.reversed().reduce("", { $0 + $1.description})})
            .reduce("", { $0.isEmpty ? $1 : "\($0) \($1)" })

    }
}
```

