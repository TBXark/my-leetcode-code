# 20. Valid Parentheses

### 2017-02-27

Given a string containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

The brackets must close in the correct order, `"()"` and `"()[]{}"` are all valid but `"(]"` and `"([)]"` are not.



# Solution

```swift
class Solution {
    func isValid(_ s: String) -> Bool {
        var chars = [Character]()
        for c in s.characters {
            switch c {
            case "(", "[", "{":
                chars.append(c)
            case ")":
                guard let l = chars.last, l == "(" else { return false }
                chars.removeLast()
            case "]":
                guard let l = chars.last, l == "["else { return false }
                chars.removeLast()
            case "}":
                guard let l = chars.last, l == "{" else { return false }
                chars.removeLast()
            default:
                return false
            }
        }
        return chars.isEmpty

    }
}
```

