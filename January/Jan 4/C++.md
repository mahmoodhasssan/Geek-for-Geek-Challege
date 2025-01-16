
# *04. Count All Triplets with Given Sum in Sorted Array*

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/problems/count-all-triplets-with-given-sum-in-sorted-array/1)

## Problem Description

You are given a sorted array `arr[]` of size `n` and an integer `target`. Your task is to count the number of triplets `(i, j, k)` such that:  
- `i < j < k`  
- `arr[i] + arr[j] + arr[k] == target`

## Examples:

**Input:**  
`arr[] = [-3, -1, -1, 0, 1, 2]`, `target = -2`  
**Output:**  
`4`  
**Explanation:**  
The triplets are:  
- `arr[0] + arr[3] + arr[4] = -3 + 0 + 1 = -2`  
- `arr[0] + arr[1] + arr[5] = -3 + (-1) + 2 = -2`  
- `arr[0] + arr[2] + arr[5] = -3 + (-1) + 2 = -2`  
- `arr[1] + arr[2] + arr[3] = -1 + (-1) + 0 = -2`



**Input:**  
`arr[] = [-2, 0, 1, 1, 5]`, `target = 1`  
**Output:**  
`0`  
**Explanation:**  
No triplet adds up to `1`.



### Constraints:
- $`3 ≤ arr.size() ≤ 10^3`$
- $`-10^5 ≤ arr[i], target ≤ 10^5`$



## Code (C++)

```cpp
class Solution {
public:
    int countTriplets(vector<int>& arr, int target) {
        int n = arr.size(), res = 0;
        for (int i = 0; i < n - 2; ++i) {
            int left = i + 1, right = n - 1;
            while (left < right) {
                int sum = arr[i] + arr[left] + arr[right];
                if (sum < target) {
                    ++left;
                } else if (sum > target) {
                    --right;
                } else {
                    if (arr[left] == arr[right]) {
                        int count = right - left + 1;
                        res += (count * (count - 1)) / 2;
                        break;
                    } else {
                        int cnt1 = 1, cnt2 = 1;
                        while (left + 1 < right && arr[left] == arr[left + 1]) ++left, ++cnt1;
                        while (right - 1 > left && arr[right] == arr[right - 1]) --right, ++cnt2;
                        res += cnt1 * cnt2;
                        ++left;
                        --right;
                    }
                }
            }
        }
        return res;
    }
};
```
