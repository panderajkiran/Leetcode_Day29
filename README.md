# Leetcode_Day29
# Day 29 – Set Matrix Zeroes

## LeetCode Problem
**73. Set Matrix Zeroes**

**Difficulty:** Medium

## Problem
Given an `m x n` integer matrix, if an element is `0`, set its entire row and column to `0`.

The changes must be made **in-place**.

## Approach

I used two boolean arrays:

- `row[]` → keeps track of which rows contain `0`
- `col[]` → keeps track of which columns contain `0`

### Steps

1. Traverse the entire matrix and find all `0`s.
2. Mark the corresponding row and column as `true`.
3. Traverse the matrix again:
   - If the row is marked, set the element to `0`.
   - If the column is marked, set the element to `0`.

This avoids accidentally using newly created zeroes to affect additional rows or columns.

## Complexity

- **Time Complexity:** `O(m × n)`
- **Space Complexity:** `O(m + n)`

## Key Learning

The important part of this problem was realizing that modifying the matrix immediately while finding zeroes can create incorrect results.

Instead, first remember **where the zeroes are**, and only then modify the matrix.

## Java Solution

```java
class Solution {
    public void setZeroes(int[][] matrix) {
        int n = matrix.length;
        int m = matrix[0].length;

        boolean[] row = new boolean[n];
        boolean[] col = new boolean[m];

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if (matrix[i][j] == 0) {
                    row[i] = true;
                    col[j] = true;
                }
            }
        }

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if (row[i] == true) {
                    matrix[i][j] = 0;
                }
            }
        }

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if (col[j] == true) {
                    matrix[i][j] = 0;
                }
            }
        }
    }
}
