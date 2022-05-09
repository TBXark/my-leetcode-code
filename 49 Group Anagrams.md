# 49. Group Anagrams

### 2017-02-17

Given an array of strings, group anagrams together.

For example, given: `["eat", "tea", "tan", "ate", "nat", "bat"]`, 
Return:

```
[
  ["ate", "eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```

**Note:** All inputs will be in lower-case.



# Solution

```swift


class Solution {
    
    func groupAnagrams(_ strs: [String]) -> [[String]] {
        var res = [String: [String]]()
        for str in strs {
            let k = str.characters.sorted().map({ "\($0)"}).reduce("", +)
            var temp = res[k] ?? [String]()
            temp.append(str)
            res[k] = temp
        }
        return Array(res.values)
    }
}
```



