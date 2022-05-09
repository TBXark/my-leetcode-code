# 290. Word Pattern

### 2017-03-13

Given a `pattern` and a string `str`, find if `str` follows the same pattern.

Here **follow** means a full match, such that there is a bijection between a letter in `pattern` and a **non-empty** word in `str`.

**Examples:**

1. pattern = `"abba"`, str = `"dog cat cat dog"` should return true.
2. pattern = `"abba"`, str = `"dog cat cat fish"` should return false.
3. pattern = `"aaaa"`, str = `"dog cat cat dog"` should return false.
4. pattern = `"abba"`, str = `"dog dog dog dog"` should return false.

**Notes:**
You may assume `pattern` contains only lowercase letters, and `str` contains lowercase letters separated by a single space.



# Solution

```swift
class Solution {
    func wordPattern(_ pattern: String, _ str: String) -> Bool {
        let array = str.components(separatedBy: " ")
        guard pattern.characters.count == array.count else { return false }
        var dict = [String: String]()
        for (i, char) in pattern.characters.enumerated() {
            let word = array[i]
            let c = char.description
            if let test = dict[c] {
                guard test == word else { return false }
            } else  {
                if dict.values.contains(word) {
                    return false
                } else {
                    dict[c] = word
                }
            }
        }
        return true

    }
}
```

