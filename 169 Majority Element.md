# 169. Majority Element

### 2017-03-01

Given an array of size *n*, find the majority element. The majority element is the element that appears **more than** `⌊ n/2 ⌋` times.

You may assume that the array is non-empty and the majority element always exist in the array.



# Solution*

```swift
class Solution {
    func majorityElement(_ nums: [Int]) -> Int {
        var ele = nums[0]
        var count = 1
        for i in 1..<nums.count {
            if count == 0 {
                ele = nums[i]
                count += 1
            } else if nums[i] == ele {
                count += 1
            } else {
                count -= 1
            }
        }
        return ele

    }
}	
```

