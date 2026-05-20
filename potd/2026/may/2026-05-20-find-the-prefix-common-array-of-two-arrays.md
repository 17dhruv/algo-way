# Find the Prefix Common Array of Two Arrays

## Problem Link

https://leetcode.com/problems/find-the-prefix-common-array-of-two-arrays/description/?envType=daily-question&envId=2026-05-20

## Intuition

For every index `i`, we need to know how many values have appeared in both
prefixes `A[0...i]` and `B[0...i]`.

Since `A` and `B` are permutations, each number appears exactly once in each
array. A number becomes common as soon as we have seen it in both arrays.

## Approach: Bitmask

Instead of repeatedly comparing prefixes, track the values seen so far in both
arrays using two bitmasks:

- `maskA` stores all numbers already seen in `A`.
- `maskB` stores all numbers already seen in `B`.
- At each index, set the corresponding bits for `A[i]` and `B[i]`.
- The common values are represented by `maskA & maskB`.
- The answer for that index is the number of set bits in this intersection.

The result can be written directly into `B`, so no extra result array is needed.

## Complexity

- Time Complexity: `O(n)`
- Space Complexity: `O(1)`

## Code

```cpp
class Solution {
public:
    vector<int> findThePrefixCommonArray(vector<int>& A, vector<int>& B) {
        uint64_t maskA = 0;
        uint64_t maskB = 0;

        for (uint8_t i = 0; i < A.size(); i++) {
            maskA |= 1ULL << A[i];
            maskB |= 1ULL << B[i];
            B[i] = __builtin_popcountll(maskA & maskB);
        }

        return B;
    }
};
```
