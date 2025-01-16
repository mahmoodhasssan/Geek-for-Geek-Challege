# *1. Print Anagrams Together*

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/problems/print-anagrams-together/1)

## Problem Description

You are given an array `arr[]` of strings. Your task is to group the anagrams together and return all such groups. The groups must be created in order of their appearance in the original array.

Note: The final output will be in lexicographic order.

## Examples:

**Input:**  
`arr[] = ["act", "god", "cat", "dog", "tac"]`  
**Output:**  
`[["act", "cat", "tac"], ["god", "dog"]]`  
Explanation:  
There are 2 groups of anagrams:
- "god", "dog" make group 1
- "act", "cat", "tac" make group 2

**Input:**  
`arr[] = ["no", "on", "is"]`  
**Output:**  
`[["is"], ["no", "on"]]`  
Explanation:  
There are 2 groups of anagrams:
- "is" makes group 1
- "no", "on" make group 2

**Input:**  
`arr[] = ["listen", "silent", "enlist", "abc", "cab", "bac", "rat", "tar", "art"]`  
**Output:**  
`[["abc", "cab", "bac"], ["listen", "silent", "enlist"], ["rat", "tar", "art"]]`  
Explanation:  
- Group 1: "abc", "bac", and "cab" are anagrams.
- Group 2: "listen", "silent", and "enlist" are anagrams.
- Group 3: "rat", "tar", and "art" are anagrams.

### Constraints:
- `1 <= arr.size() <= 100`
- `1 <= arr[i].size() <= 10`
### C++ Code
  ```cpp
class Solution {
public:
    vector<vector<string>> anagrams(vector<string>& arr) {
        unordered_map<string, vector<string>> umap;
        for (string s : arr) {
            string sorted_s = s;
            sort(sorted_s.begin(), sorted_s.end());
            umap[sorted_s].push_back(s);
        }
        vector<vector<string>> result;
        for (auto it : umap)
            result.push_back(it.second);
        return result;
    }
};
```
