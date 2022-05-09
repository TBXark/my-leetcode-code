# 42. Trapping Rain Water

### 2017-02-15

Given *n* non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it is able to trap after raining.

For example, 
Given `[0,1,0,2,1,0,1,3,2,1,2,1]`, return `6`.

![](http://www.leetcode.com/wp-content/uploads/2012/08/rainwatertrap.png)



# Solution

```swift
class Solution {
    func trap(_ height: [Int]) -> Int {
        guard height.count >= 3 else { return 0 }
        var total = 0
        var flags = [Int]()
        let count = height.count - 1
        for i in 0...count {
            let l = i == 0 ? true : height[i] >= height[i - 1]
            let r = i == count ? true : height[i] >= height[i + 1]
            if  l && r {
                while flags.count >= 2,
                    height[flags[flags.count - 2]] >= height[flags.last!],
                    height[flags.last!] <= height[i] {
                    flags.removeLast()
                }
                flags.append(i)
            }
        }
        guard flags.count > 0 else { return 0}
        for i in 0..<(flags.count - 1) {
            let a = flags[i]
            let b = flags[i+1]
            var h = 0
            let minH = min(height[a], height[b])
            for j in a...b {
                let th = minH - height[j]
                if th > 0 { h += th }
            }
            total += h
        }
        return total
    }
}
```

