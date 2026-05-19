# Minimum Common Value

## Problem Link

https://leetcode.com/problems/minimum-common-value/description/?envType=daily-question&envId=2026-05-19

## Approach: Two Pointers

Both arrays are sorted, so we can traverse them together using two pointers.

- If both elements are equal, that value is the smallest common element.
- If `nums1[i] < nums2[j]`, move `i` forward.
- Otherwise, move `j` forward.

This works because smaller elements in a sorted array cannot match larger elements later unless we move past them.

## Complexity

- Time Complexity: `O(n + m)`
- Space Complexity: `O(1)`

## Code

```cpp
class Solution {
public:
    int getCommon(vector<int>& nums1, vector<int>& nums2) {
        int i = 0;
        int j = 0;

        while (i < nums1.size() && j < nums2.size()) {
            if (nums1[i] == nums2[j]) {
                return nums1[i];
            }

            if (nums1[i] < nums2[j]) {
                i++;
            } else {
                j++;
            }
        }

        return -1;
    }
};
```
