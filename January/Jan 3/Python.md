# *03. Count Subarrays with Given XOR*

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/problems/count-subarray-with-given-xor/1)



## **Problem Description**

Given an array of integers `arr[]` and an integer `k`, count the number of subarrays whose XOR is equal to `k`.



## **Examples**

### **Example 1**

**Input:**  
`arr = [4, 2, 2, 6, 4], k = 6`  
**Output:**  
`4`  

**Explanation:**  
The subarrays having XOR of their elements as `6` are:  
1. `[4, 2]`  
2. `[4, 2, 2, 6, 4]`  
3. `[2, 2, 6]`  
4. `[6]`

Hence, the output is `4`.



### **Example 2**

**Input:**  
`arr = [5, 6, 7, 8, 9], k = 5`  
**Output:**  
`2`  

**Explanation:**  
The subarrays having XOR of their elements as `5` are:  
1. `[5]`  
2. `[5, 6, 7, 8, 9]`

Hence, the output is `2`.



## **Constraints**

- $`1 ≤ arr.size() ≤ 10^5`$
- $`0 ≤ arr[i] ≤ 10^5`$
- $`0 ≤ k ≤ 10^5`$

## Code (Python)

```python
class Solution:
    def subarrayXor(self, arr, k):
        res, prefXOR = 0, 0
        count = {0: 1}
        for val in arr:
            prefXOR ^= val
            res += count.get(prefXOR ^ k, 0)
            count[prefXOR] = count.get(prefXOR, 0) + 1
        return res
```
