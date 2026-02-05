**Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.**
**The overall run time complexity should be O(log (m+n)).**

 
```swift
Example 1:

Input: nums1 = [1,3], nums2 = [2]
Output: 2.00000
Explanation: merged array = [1,2,3] and median is 2.
Example 2:

Input: nums1 = [1,2], nums2 = [3,4]
Output: 2.50000
Explanation: merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.
 ```

**Constraints:**

```swift
nums1.length == m
nums2.length == n
0 <= m <= 1000
0 <= n <= 1000
1 <= m + n <= 2000
-106 <= nums1[i], nums2[i] <= 106
```

```swift
class Solution {
    func findMedianSortedArrays(_ nums1: [Int], _ nums2: [Int]) -> Double {
        //
        if nums1.count > nums2.count {
            return findMedianSortedArrays(nums2, nums1)
        }
        let m: Int = nums1.count
        let n: Int = nums2.count
        //
        var low: Int = 0
        var high: Int = m
        //
        while(low <= high) {
            var i = (low + high) / 2
            var j = (n + m + 1) / 2 - i

            var leftA = i == 0 ? Int.min : nums1[i - 1]
            var rightA = i == m ? Int.max : nums1[i]

            var leftB = j == 0 ? Int.min : nums2[j - 1]
            var rightB = j == n ? Int.max : nums2[j]

            if leftA <= rightB && leftB <= rightA {
                if (m + n) % 2 == 0 {
                    return Double(max(leftA, leftB) + min(rightA, rightB)) / 2.0
                } else {
                    return Double(max(leftA, leftB))
                }
            } else if leftA > rightB {
                high = i - 1
            } else {
                low = i + 1
            }
        }
        //
        return 0.0
    }
}
```
