# *06. Sum Pair Closest to Target*

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/problems/pair-in-array-whose-sum-is-closest-to-x1124/1)

## Problem Description

You are given an array `arr[]` and a number `target`. Your task is to find a pair of elements `(a, b)` in `arr[]` where `a <= b` whose sum is closest to the target. If there are multiple such pairs, return the pair with the maximum absolute difference. If no such pair exists, return an empty array.

## Examples:

**Input:**  
`arr[] = [10, 30, 20, 5], target = 25`  
**Output:**  
`[5, 20]`

**Input:**  
`arr[] = [5, 2, 7, 1, 4], target = 10`  
**Output:**  
`[2, 7]`  
Explanation: As both `(4, 7)` and `(2, 7)` are closest to the target 10, the absolute difference of `(2, 7)` is 5 and `(4, 7)` is 3. Hence, `[2, 7]` is the correct pair.

**Input:**  
`arr[] = [10], target = 10`  
**Output:**  
`[]`  
Explanation: The array contains only one element, so no valid pair can be formed.

### Constraints:
- $`1 <= arr.size() <= 2*10^5`$
- $`0 <= target <= 2*10^5`$
- $`0 <= arr[i] <= 10^5`$
## Code (Python)

```python
class Solution:
    def sumClosest(self, arr, target):
        arr.sort()
        l, r, minDiff, res = 0, len(arr) - 1, float('inf'), []
        while l < r:
            s = arr[l] + arr[r]
            if abs(target - s) < minDiff:
                minDiff, res = abs(target - s), [arr[l], arr[r]]
            l += s < target
            r -= s >= target
        return res
```
