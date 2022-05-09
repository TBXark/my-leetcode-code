# 213. House Robber II

### 2020-07-31

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed. All houses at this place are **arranged in a circle.** That means the first house is the neighbor of the last one. Meanwhile, adjacent houses have security system connected and **it will automatically contact the police if two adjacent houses were broken into on the same night**.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight **without alerting the police**.

**Example 1:**

```
Input: [2,3,2]
Output: 3
Explanation: You cannot rob house 1 (money = 2) and then rob house 3 (money = 2),
             because they are adjacent houses.
```

**Example 2:**

```
Input: [1,2,3,1]
Output: 4
Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
             Total amount you can rob = 1 + 3 = 4.
```



# Solution

```swift

class Solution {
    
    private func robLine(start: Int, end: Int, nums: [Int]) -> Int {
        var cache = [Int: Int]()
        for i in start..<end {
            let x = end - i - 1 + start
            cache[x] = max(nums[x] + (cache[x + 2] ?? 0), cache[x + 1] ?? 0)
        }
        return cache[start] ?? 0
    }
    
    func rob(_ nums: [Int]) -> Int {
        guard nums.count > 0 else {
            return 0
        }
        if nums.count / 2 == 0 {
            return robLine(start: 0, end: nums.count, nums: nums)
        } else {
            return max(robLine(start: 0, end: nums.count - 1, nums: nums), robLine(start: 1, end: nums.count, nums: nums))
        }
    }
}

```
