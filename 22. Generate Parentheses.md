# 22. Generate Parentheses

### 2022-05-09

Given `n` pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

 

Example 1:
```
Input: n = 3
Output: ["((()))","(()())","(())()","()(())","()()()"]
```

Example 2:
```
Input: n = 1
Output: ["()"]
```



# Solution

```swift
class Solution {
    
    private func generateParenthesis(left: Int, right: Int, max: Int, str: String, result: inout [String])  {
        if left == max, right == max {
            result.append(str)
            return
        }
        if left < max {
            generateParenthesis(left: left + 1, right: right, max: max, str: str + "(", result: &result)
        }
        if left > right {
            generateParenthesis(left: left, right: right + 1, max: max, str: str + ")", result: &result)
        }
    }
    
    func generateParenthesis(_ n: Int) -> [String] {
        var temp = [String]()
        generateParenthesis(left: 0, right: 0, max: n, str: "", result: &temp)
        return temp
    }
}

```
