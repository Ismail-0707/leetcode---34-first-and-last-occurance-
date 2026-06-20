# LeetCode 34 - Find First and Last Position of Element in Sorted Array

## Problem Statement

Given a sorted integer array `nums` and an integer `target`, find the starting and ending positions of the target value.

If the target is not found in the array, return `[-1, -1]`.

### Example 1

Input:
nums = [5,7,7,8,8,10], target = 8

Output:
[3,4]

### Example 2

Input:
nums = [5,7,7,8,8,10], target = 6

Output:
[-1,-1]

### Example 3

Input:
nums = [], target = 0

Output:
[-1,-1]

---

## Approach (Brute Force)

1. Initialize the result array as `[-1, -1]`.
2. Traverse the array from left to right.
3. When the target is found:
   - If it is the first occurrence, store its index in `res[0]`.
   - Continuously update `res[1]` with the current index.
4. After traversal:
   - If the target was found, `res` contains the first and last positions.
   - Otherwise, return `[-1, -1]`.

---

## Java Solution

```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int[] res = {-1, -1};

        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == target) {
                if (res[0] == -1) {
                    res[0] = i;
                }
                res[1] = i;
            }
        }

        return res;
    }
}
```

---

## Dry Run

Input:

nums = [5,7,7,8,8,10]
target = 8

| i | nums[i] | res |
|---|----------|------|
| 0 | 5 | [-1,-1] |
| 1 | 7 | [-1,-1] |
| 2 | 7 | [-1,-1] |
| 3 | 8 | [3,3] |
| 4 | 8 | [3,4] |
| 5 | 10 | [3,4] |

Output:

[3,4]

---

## Complexity Analysis

### Time Complexity
- O(n)
- We traverse the array once.

### Space Complexity
- O(1)
- Only the result array is used.

---

## Key Insight

The brute-force solution works by scanning the entire array and tracking the first and last occurrence of the target. However, since the array is sorted, an optimal Binary Search solution can solve the problem in **O(log n)** time.
