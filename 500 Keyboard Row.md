# 500. Keyboard Row

### 2017-03-12

Given a List of words, return the words that can be typed using letters of **alphabet** on only one row's of American keyboard like the image below.

![American keyboard](https://leetcode.com/static/images/problemset/keyboard.png)

**Example 1:**

```
Input: ["Hello", "Alaska", "Dad", "Peace"]
Output: ["Alaska", "Dad"]

```

**Note:**

1. You may use one character in the keyboard more than once.
2. You may assume the input string will only contain letters of alphabet.



# Solution

```swift
class Solution {
    func findWords(_ words: [String]) -> [String] {
        var res = [String]()
        let row = ["[qwertyuiop]", "[asdfghjkl]", "[zxcvbnm]"].flatMap({
            try? RegularExpression(pattern: "^[\($0)]{0,}$", options: [.caseInsensitive])
        })
        for str in words {
            let range = NSRange.init(location: 0, length: str.utf8.count)
            for regx in row {
                if regx.matches(in: str, options: [], range: range).count > 0 {
                    res.append(str)
                    break
                }
            }
        }
        return res
    }
}
```

