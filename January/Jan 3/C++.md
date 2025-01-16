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
## Code (C++)

```cpp
class Solution {
public:
    long subarrayXor(vector<int> &arr, int k) {
        long res = 0, prefXOR = 0;
        unordered_map<int, int> mp;
        for (int val : arr) {
            prefXOR ^= val;
            res += mp[prefXOR ^ k] + (prefXOR == k);
            mp[prefXOR]++;
        }
        return res;
    }
};

```
