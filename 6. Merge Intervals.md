**Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an 
array of the non-overlapping intervals that cover all the intervals in the input.**

 ```swift
Example 1:

Input: intervals = [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
Explanation: Since intervals [1,3] and [2,6] overlap, merge them into [1,6].
Example 2:

Input: intervals = [[1,4],[4,5]]
Output: [[1,5]]
Explanation: Intervals [1,4] and [4,5] are considered overlapping.
Example 3:

Input: intervals = [[4,7],[1,4]]
Output: [[1,7]]
Explanation: Intervals [1,4] and [4,7] are considered overlapping.
```

**Constraints:**

```swift
1 <= intervals.length <= 104
intervals[i].length == 2
0 <= starti <= endi <= 104
```

**Solution**

```swift
class Solution {
    func merge(_ intervals: [[Int]]) -> [[Int]] {
        //
        if intervals.isEmpty {return []}
        //
        let sorted = intervals.sorted{$0[0] < $1[0]}
        var current = sorted[0]
        var output: [[Int]] = []
        //
        for (index, interval) in sorted.enumerated() where index > 0 {
            if interval[0] <= current[1] {
                current[1] = max(interval[1], current[1])
            } else {
                output.append(current)
                current = interval
            }
        }
        //
        output.append(current)
        //
        return output
    }
}
```
