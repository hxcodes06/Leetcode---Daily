# Day 1 - Shift 2D Grid

## LeetCode Problem

**Problem Number:** 1260

**Difficulty:** Easy

---

## Problem Statement

Given a 2D grid of size `m × n` and an integer `k`, shift the grid `k` times.

During one shift:

- Each element moves one position to the right.
- The last element of a row moves to the first column of the next row.
- The last element of the grid moves to the first position.

---

## Example

### Input

```text
grid = [[1,2,3],
        [4,5,6],
        [7,8,9]]

k = 1
```

### Output

```text
[[9,1,2],
 [3,4,5],
 [6,7,8]]
```

---

# My Approach

Instead of shifting the matrix one step at a time, I treated the entire 2D grid as a single 1D array.

Each element was converted into a 1D index.

After adding `k` to the index and taking modulo with the total number of elements, I converted the index back into a 2D position.

This avoids repeated shifting and completes the task in a single traversal.

---

# Strategy

1. Calculate the total number of elements.
2. Reduce unnecessary shifts using modulo.
3. Convert each element to a 1D index.
4. Compute its new position.
5. Convert back to row and column.
6. Store it in the answer grid.

---

# Algorithm

- Find number of rows and columns.
- Calculate total elements.
- Perform modulo operation on `k`.
- Traverse every element once.
- Compute the new index.
- Place the element in the new position.
- Return the shifted grid.

---

# Time Complexity

**O(m × n)**

---

# Space Complexity

**O(m × n)**

---

# Python Solution

See `solution.py`

---

# Output

See `output.png`

---

# What I Learned

- Converting between 2D and 1D indexing.
- Using modulo for circular movement.
- Solving the problem without repeated shifting.
- Writing cleaner and more efficient code.
