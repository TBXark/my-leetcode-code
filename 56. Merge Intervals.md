# 56. Merge Intervals

### 2017-03-28

Given a collection of intervals, merge all overlapping intervals.

For example,
Given `[1,3],[2,6],[8,10],[15,18]`,
return `[1,6],[8,10],[15,18]`.



# Solution

```swift
/**
 * Definition for an interval.
 * public class Interval {
 *   public var start: Int
 *   public var end: Int
 *   public init(_ start: Int, _ end: Int) {
 *     self.start = start
 *     self.end = end
 *   }
 * }
 */
class Solution {
    func merge(_ intervals: [Interval]) -> [Interval] {
        guard intervals.count > 0 else { return [] }
        var temp = intervals.sorted { $0.0.start < $0.1.start}
        var res = [Interval]()
        var start = temp[0].start
        var end = temp[0].end
        for iv in  temp {
            if iv.start <= end {
                end = max(iv.end, end)
            } else {
                res.append(Interval(start, end))
                start = iv.start
                end = iv.end
            }
        }
        res.append(Interval(start, end))
        return res

    }
}
```

