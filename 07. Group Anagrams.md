**Given an array of strings strs, group the anagrams together. You can return the answer in any order.**


```swift
Example 1:

Input: strs = ["eat","tea","tan","ate","nat","bat"]

Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
```
**Explanation:**
```swift
There is no string in strs that can be rearranged to form "bat".
The strings "nat" and "tan" are anagrams as they can be rearranged to form each other.
The strings "ate", "eat", and "tea" are anagrams as they can be rearranged to form each other.
```

```swift
Example 2:

Input: strs = [""]

Output: [[""]]

Example 3:

Input: strs = ["a"]

Output: [["a"]]
```
 
**Constraints:**
```swift
1 <= strs.length <= 104
0 <= strs[i].length <= 100
strs[i] consists of lowercase English letters.
```

**Solution**

```swift
class Solution {
    func groupAnagrams(_ strs: [String]) -> [[String]] {
        //
        var map: [[Int]: [String]] = [:]
        //
        for word in strs {
            var frequencyArr = Array(repeating: 0, count: 26)
            for ch in word {
                frequencyArr[Int(ch.asciiValue! - Character("a").asciiValue!)] += 1
            }
            map[frequencyArr, default: []].append(word)
        }
        //
        return Array(map.values)
    }
}
```
