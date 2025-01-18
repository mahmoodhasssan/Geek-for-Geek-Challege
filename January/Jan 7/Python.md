# *07. Pair with Given Sum in a Sorted Array*
## Code (Python)

```python
class Solution:
    def countPairs(self, arr, target):
        freq = {}
        res = 0

        for num in arr:
            res += freq.get(target - num, 0)
            freq[num] = freq.get(num, 0) + 1

        return res
```
