# *02. Subarrays with Sum K*

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/subarrays-with-sum-k/1)

## Problem Description

Given an unsorted array of integers, find the number of continuous subarrays having a sum exactly equal to a given number `k`.

**Examples:**

Input:  
```
arr = [10, 2, -2, -20, 10], k = -10
```
Output:  
```
3
```
Explanation: Subarrays: `arr[0...3]`, `arr[1...4]`, and `arr[3...4]` have a sum exactly equal to `-10`.

Input:  
```
arr = [9, 4, 20, 3, 10, 5], k = 33
```
Output:  
```
2
```
Explanation: Subarrays: `arr[0...2]` and `arr[2...4]` have a sum exactly equal to `33`.

Input:  
```
arr = [1, 3, 5], k = 0
```
Output:  
```
0
```
Explanation: No subarray has a sum of `0`.

**Constraints:**

- $\(1 \leq \text{arr.size()} \leq 10^5\)$
- $\(-10^3 \leq \text{arr[i]} \leq 10^3\)$
- $\(-10^7 \leq k \leq 10^7\)$

## Code (Python)

```python
class Solution:
    def countSubarrays(self, arr, k):
        prefix_sum_count = {0: 1}
        sum_, count = 0, 0

        for num in arr:
            sum_ += num
            count += prefix_sum_count.get(sum_ - k, 0)
            prefix_sum_count[sum_] = prefix_sum_count.get(sum_, 0) + 1

        return count
```
