# Day 7 - Longest Substring Without Repeating Characters

### LeetCode Problem

**Problem Number:** 3

**Difficulty:** Medium

---

## Problem Statement

Given a string `s`, find the length of the **longest substring** that contains no repeating characters.

A **substring** is a contiguous sequence of characters within a string.

Return the length of the longest substring without duplicate characters.

---

## Example

### Input

```text
s = "abcabcbb"
```

### Output

```text
3
```

**Explanation:**

The longest substring without repeating characters is `"abc"`, which has a length of **3**.

---

### Input

```text
s = "bbbbb"
```

### Output

```text
1
```

**Explanation:**

The longest substring is `"b"` since every character is the same.

---

### Input

```text
s = "pwwkew"
```

### Output

```text
3
```

**Explanation:**

The longest substring is `"wke"` with a length of **3**.

---

## My Approach

For every character in the string, I treated it as the starting point of a new substring.

I used a `set` to keep track of the characters that had already appeared in the current substring. Then I kept extending the substring one character at a time.

If I encountered a character that was already present in the set, I stopped checking that substring because it contained a duplicate. Otherwise, I added the character to the set and updated the maximum length found so far.

Although this isn't the most optimized solution, it's simple to understand and works well for learning how substring checking works.

---

## Strategy

- Start from every possible index in the string.
- Use a `set` to store the unique characters in the current substring.
- Continue expanding the substring until a duplicate character is found.
- Update the maximum substring length whenever a longer valid substring is found.
- Return the maximum length.

---

## Algorithm

1. Find the length of the string.
2. Initialize the answer as `0`.
3. Loop through every character as the starting index.
4. Create an empty `set` for each starting position.
5. Extend the substring one character at a time.
6. If the character already exists in the set, stop checking that substring.
7. Otherwise, add the character to the set and update the maximum length.
8. Return the maximum length.

---

## Python Solution

```python
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        n = len(s)
        res = 0

        for i in range(n):
            seen = set()

            for j in range(i, n):
                if s[j] in seen:
                    break
                else:
                    seen.add(s[j])
                    res = max(res, j - i + 1)

        return res
```

---

## Time Complexity

**O(n²)**

For every starting index, the algorithm checks the remaining characters until a duplicate is found.

---

## Space Complexity

**O(n)**

In the worst case, the `set` stores all unique characters in the current substring.

---

## What I Learned

- How to generate every possible substring starting from each index.
- Using a `set` to efficiently detect duplicate characters.
- Updating the maximum answer while traversing the string.
- The difference between a **substring** (continuous) and a **subsequence** (not necessarily continuous).
- How a brute-force approach works before moving on to more optimized solutions like the Sliding Window technique.

---

**Happy Coding! 🚀**
