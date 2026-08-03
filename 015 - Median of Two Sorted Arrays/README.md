# Day 15 - Median of Two Sorted Arrays

### LeetCode Problem

**Problem Number:** 4

**Difficulty:** Hard

---

## Problem Statement

You are given two sorted arrays `nums1` and `nums2` of sizes `m` and `n`.

Your task is to find the **median** of the two sorted arrays.

The median is the middle value of a sorted array. If the total number of elements is even, the median is the average of the two middle elements.

---

## Example

### Input

```text
nums1 = [1,3]
nums2 = [2]
```

### Output

```text
2.00000
```

**Explanation:**

Merged array = `[1,2,3]`

The middle element is `2`, so the median is **2.0**.

---

### Input

```text
nums1 = [1,2]
nums2 = [3,4]
```

### Output

```text
2.50000
```

**Explanation:**

Merged array = `[1,2,3,4]`

The two middle elements are `2` and `3`.

Median = `(2 + 3) / 2 = 2.5`

---

## My Approach

Instead of creating a completely merged array, I used **two pointers** to traverse both sorted arrays simultaneously.

At every step, I selected the smaller element from the two arrays and kept track of the current and previous selected values. Since the median only depends on the middle element(s), there is no need to store the entire merged array.

After reaching the middle position:

- If the total number of elements is odd, I returned the current element.
- If the total number of elements is even, I returned the average of the current and previous elements.

This approach saves extra space while still correctly finding the median.

---

## Strategy

- Initialize two pointers for both arrays.
- Compare the current elements of both arrays.
- Pick the smaller element and move its pointer.
- Keep track of the last two selected elements.
- Continue until reaching the middle of the combined arrays.
- Return the median based on whether the total length is odd or even.

---

## Algorithm

1. Initialize two pointers for both arrays.
2. Maintain two variables to store the current and previous selected elements.
3. Traverse both arrays until the middle position is reached.
4. Always choose the smaller element from the two arrays.
5. If one array is exhausted, continue with the other.
6. If the total number of elements is odd, return the current element.
7. Otherwise, return the average of the current and previous elements.

---

## Python Solution

```python
class Solution:
    def findMedianSortedArrays(self, nums1, nums2):
        n = len(nums1)
        m = len(nums2)
        i = 0
        j = 0
        m1 = 0
        m2 = 0

        # Find median
        for count in range(0, (n + m) // 2 + 1):
            m2 = m1

            if i < n and j < m:
                if nums1[i] > nums2[j]:
                    m1 = nums2[j]
                    j += 1
                else:
                    m1 = nums1[i]
                    i += 1

            elif i < n:
                m1 = nums1[i]
                i += 1

            else:
                m1 = nums2[j]
                j += 1

        if (n + m) % 2 == 1:
            return float(m1)
        else:
            return (float(m1) + float(m2)) / 2.0
```

---

## Time Complexity

**O(m + n)**

In the worst case, the algorithm traverses elements from both arrays until the median position is reached.

---

## Space Complexity

**O(1)**

Only a few variables are used, and no extra array is created.

---

## What I Learned

- How to merge two sorted arrays using the two-pointer technique.
- Finding the median without storing the merged array.
- Handling both odd and even total lengths.
- Using pointers efficiently to reduce extra space.
- Solving array traversal problems with a simple and clean approach.

> **Note:** Although the problem asks for an **O(log(m + n))** solution, this implementation uses a straightforward **two-pointer approach** with **O(m + n)** time complexity. It is easier to understand and correctly computes the median, making it a good stepping stone before learning the optimal binary search solution.

---

**Happy Coding! 🚀**
