````markdown
# Day 10 - Longest Common Prefix

### LeetCode Problem

**Problem Number:** 14

**Difficulty:** Easy

---

## Problem Statement

Given an array of strings `strs`, find the **longest common prefix** shared among all the strings.

If there is no common prefix, return an empty string `""`.

---

## Example

### Input

```text
strs = ["flower", "flow", "flight"]
```

### Output

```text
"fl"
```

---

### Input

```text
strs = ["dog", "racecar", "car"]
```

### Output

```text
""
```

**Explanation:**

The three strings do not share any common starting characters, so the answer is an empty string.

---

## My Approach

Instead of comparing every string with each other, I first sorted the array of strings.

After sorting, the strings that are most different appear at the beginning and the end of the array. This means the longest common prefix of the entire array will also be the common prefix between the **first** and **last** strings.

I then compared these two strings character by character. As long as the characters matched, I added them to the answer. The moment a mismatch occurred, I stopped because no further common prefix was possible.

This approach reduces unnecessary comparisons and keeps the solution simple.

---

## Strategy

- Sort the array of strings.
- Compare the first and last strings after sorting.
- Check characters one by one from the beginning.
- Build the common prefix until a mismatch is found.
- Return the final prefix.

---

## Algorithm

1. Sort the array of strings.
2. Initialize an empty string to store the prefix.
3. Compare the first and last strings character by character.
4. If the characters match, add them to the prefix.
5. Stop when a mismatch occurs.
6. Return the longest common prefix.

---

## Python Solution

```python
class Solution:
    def longestCommonPrefix(self, strs):
        strs.sort()
        s = ""
        i = 0
        length = len(strs)

        while i < len(strs[0]):
            if strs[0][i] == strs[length - 1][i]:
                s += strs[0][i]
            else:
                break
            i += 1

        return s
```

---

## Time Complexity

**O(n log n + m)**

- Sorting the array takes **O(n log n)**.
- Comparing the first and last strings takes **O(m)**, where `m` is the length of the shortest string.

---

## Space Complexity

**O(1)**

No extra data structures are used apart from the string used to store the answer.

---

## What I Learned

- How sorting can simplify string comparison problems.
- The longest common prefix of all strings can be found by comparing only the first and last strings after sorting.
- Building a string character by character until a mismatch occurs.
- Writing a clean and efficient solution without comparing every pair of strings.

---

**Happy Coding! 🚀**
````
