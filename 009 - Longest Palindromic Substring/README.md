# Day 8 - Regular Expression Matching

### LeetCode Problem

**Problem Number:** 10

**Difficulty:** Hard

---

## Problem Statement

Given an input string `s` and a pattern `p`, implement regular expression matching with support for:

- `.` → Matches any single character.
- `*` → Matches zero or more occurrences of the preceding character.

The pattern must match the **entire string**, not just a part of it.

Return `true` if the string matches the pattern; otherwise, return `false`.

---

## Example

### Input

```text
s = "aa"
p = "a"
```

### Output

```text
false
```

**Explanation:**

The pattern `"a"` matches only one character, while the input string contains two characters.

---

### Input

```text
s = "aa"
p = "a*"
```

### Output

```text
true
```

**Explanation:**

The `*` allows the character `'a'` to appear zero or more times, so `"a*"` successfully matches `"aa"`.

---

### Input

```text
s = "ab"
p = ".*"
```

### Output

```text
true
```

**Explanation:**

The `.` matches any character, and `*` allows it to repeat any number of times, so `".*"` matches the entire string.

---

## My Approach

I solved this problem using **recursion with memoization (backtracking + caching)**.

Starting from the end of both the string and the pattern, I recursively checked whether the current characters matched. Since many subproblems are repeated during recursion, I stored previously computed results in a dictionary (`cache`) to avoid unnecessary calculations.

When the current pattern character is `*`, there are two possibilities:

- Ignore the `character*` pair completely (zero occurrences).
- Use the `*` to match the current character in the string and continue checking.

For normal characters and `.`, I simply checked if they matched and moved both pointers one step backward.

Memoization makes the recursive solution much more efficient by preventing repeated work.

---

## Strategy

- Start comparing the string and pattern from the last character.
- Store solved subproblems in a cache.
- Handle base cases when either the string or pattern is exhausted.
- If the current pattern character is `*`, try both possible matching scenarios.
- For normal characters or `.`, move both pointers when they match.
- Return whether the complete string matches the complete pattern.

---

## Algorithm

1. Initialize two pointers at the end of the string and pattern.
2. Create a cache to store previously solved states.
3. If both pointers reach the beginning, return `True`.
4. Handle cases where either the string or pattern is exhausted.
5. If the current pattern character is `*`:
   - Skip the previous character and `*`.
   - Or match one character and continue recursively.
6. If the current characters match (or the pattern contains `.`), move both pointers backward.
7. Store the result in the cache.
8. Return the final answer.

---

## Python Solution

```python
class Solution:
    def isMatch(self, s: str, p: str) -> bool:
        i, j = len(s) - 1, len(p) - 1
        return self.backtrack({}, s, p, i, j)

    def backtrack(self, cache, s, p, i, j):
        key = (i, j)
        if key in cache:
            return cache[key]

        if i == -1 and j == -1:
            cache[key] = True
            return True

        if i != -1 and j == -1:
            cache[key] = False
            return cache[key]

        if i == -1 and p[j] == '*':
            k = j
            while k != -1 and p[k] == '*':
                k -= 2

            if k == -1:
                cache[key] = True
                return cache[key]

            cache[key] = False
            return cache[key]

        if i == -1 and p[j] != '*':
            cache[key] = False
            return cache[key]

        if p[j] == '*':
            if self.backtrack(cache, s, p, i, j - 2):
                cache[key] = True
                return cache[key]

            if p[j - 1] == s[i] or p[j - 1] == '.':
                if self.backtrack(cache, s, p, i - 1, j):
                    cache[key] = True
                    return cache[key]

        if p[j] == '.' or s[i] == p[j]:
            if self.backtrack(cache, s, p, i - 1, j - 1):
                cache[key] = True
                return cache[key]

        cache[key] = False
        return cache[key]
```

---

## Time Complexity

**O(m × n)**

Each unique combination of string index and pattern index is solved only once because of memoization.

---

## Space Complexity

**O(m × n)**

The cache stores results for different `(string index, pattern index)` states, and the recursion stack also contributes to the space usage.

---

## What I Learned

- How recursion can be used to solve pattern-matching problems.
- The importance of **memoization** in reducing repeated computations.
- How the `.` wildcard matches any single character.
- How `*` can represent zero or more occurrences of the preceding character.
- Breaking a complex recursive problem into smaller subproblems and storing their results for better performance.

---

**Happy Coding! 🚀**
