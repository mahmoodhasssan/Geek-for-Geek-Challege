# *05. Count Pairs Whose Sum is Less Than Target*

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/problems/count-pairs-whose-sum-is-less-than-target/1)

## Problem Description

You are given an array `arr[]` of integers and a target integer. Your task is to find the number of pairs in the array whose sum is strictly less than the given target.

## Examples:

**Input:**  
`arr[] = [7, 2, 5, 3]`, `target = 8`  
**Output:**  
`2`  
**Explanation:**  
There are 2 pairs with sum less than 8: `(2, 5)` and `(2, 3)`.

**Input:**  
`arr[] = [5, 2, 3, 2, 4, 1]`, `target = 5`  
**Output:**  
`4`  
**Explanation:**  
There are 4 pairs whose sum is less than 5: `(2, 2)`, `(2, 1)`, `(3, 1)`, and `(2, 1)`.

**Input:**  
`arr[] = [2, 1, 8, 3, 4, 7, 6, 5]`, `target = 7`  
**Output:**  
`6`  
**Explanation:**  
There are 6 pairs whose sum is less than 7: `(2, 1)`, `(2, 3)`, `(2, 4)`, `(1, 3)`, `(1, 4)`, and `(1, 5)`.

### Constraints:
- $`1 <= arr.size() <= 10^5`$
- $`0 <= arr[i] <= 10^4`$
- $`1 <= target <= 10^4`$
## Code (Python)

```python
class Solution:
    def countPairs(self, arr, target):
        arr.sort()
        l, r, ans = 0, len(arr) - 1, 0
        while l < r:
            if arr[l] + arr[r] < target: ans += (r - l); l += 1
            else: r -= 1
        return ans
```

