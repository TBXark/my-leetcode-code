# 78. Subsets

### 2022-05-10

Given an integer array `nums` of **unique** elements, return *all possible subsets (the power set)*.

The solution set **must not** contain duplicate subsets. Return the solution in **any order**.

 

**Example 1:**

```
Input: nums = [1,2,3]
Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
```

**Example 2:**

```
Input: nums = [0]
Output: [[],[0]]
```

 



# Solution

```swift
class Solution {
    func subsets(_ nums: [Int]) -> [[Int]] {
        var temp = [[Int]]()
        _subset(nums: nums, context: [], level: 0, store: &temp)
        return temp
    }
    
    private func _subset(nums: [Int], context: [Int], level: Int, store: inout [[Int]]) {
        guard nums.count > level else {
            store.append(context)
            return
        }
        _subset(nums: nums, context: context, level: level + 1, store: &store)
        var ctx = context
        ctx.append(nums[level])
        _subset(nums: nums, context: ctx, level: level + 1, store: &store)
    }
}
```


```swift
class Solution {
    func subsets(_ nums: [Int]) -> [[Int]] {
        var result = [[Int]].init([[]])
        for n in nums {
            for i in 0..<result.count {
                var temp = result[i]
                temp.append(n)
                result.append(temp)
            }
        }
        return result
    }    
}
```
