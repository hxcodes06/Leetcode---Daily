# Day 11 - Valid Parentheses

### LeetCode Problem

**Problem Number:** 20

**Difficulty:** Easy

---

## Problem Statement

Given a string `s` containing only the characters `'('`, `')'`, `'{'`, `'}'`, `'['`, and `']'`, determine whether the input string is valid.

A string is considered valid if:

- Every opening bracket has a corresponding closing bracket of the same type.
- Brackets are closed in the correct order.
- Every closing bracket has a matching opening bracket.

Return `true` if the string is valid; otherwise, return `false`.

---

## Example

### Input

```text
s = "()"
```

### Output

```text
true
```

---

### Input

```text
s = "()[]{}"
```

### Output

```text
true
```

---

### Input

```text
s = "(]"
```

### Output

```text
false
```

---

### Input

```text
s = "([])"
```

### Output

```text
true
```

---

### Input

```text
s = "([)]"
```

### Output

```text
false
```

---

## My Approach

I solved this problem using a **stack**.

Whenever I encountered an opening bracket (`(`, `{`, or `[`), I pushed it onto the stack.

When I found a closing bracket, I first checked whether the stack was empty. If it was, the string was immediately invalid because there was no matching opening bracket.

Otherwise, I popped the top element from the stack and compared it with the current closing bracket. If they didn't form a valid pair, I returned `False`.

After processing the entire string, I checked whether the stack was empty. An empty stack means every opening bracket had a matching closing bracket in the correct order.

---

## Strategy

- Create an empty stack.
- Push every opening bracket onto the stack.
- For every closing bracket:
  - Check if the stack is empty.
  - Pop the top element.
  - Verify that both brackets match.
- After processing all characters, ensure the stack is empty.

---

## Algorithm

1. Create an empty stack.
2. Traverse each character in the string.
3. If it is an opening bracket, push it onto the stack.
4. Otherwise:
   - If the stack is empty, return `False`.
   - Pop the top element.
   - Check whether it matches the current closing bracket.
5. After the loop, return `True` only if the stack is empty.

---

## Python Solution

```python
class Solution:
    def isValid(self, s: str) -> bool:
        i = 0
        a = []

        for i in range(len(s)):
            if s[i] == '(' or s[i] == '[' or s[i] == '{':
                a.append(s[i])
            else:
                if not a:
                    return False

                top = a.pop()

                if s[i] == ')' and top != '(':
                    return False
                if s[i] == ']' and top != '[':
                    return False
                if s[i] == '}' and top != '{':
                    return False

        return len(a) == 0
```

---

## Time Complexity

**O(n)**

Each bracket is pushed onto and popped from the stack at most once.

---

## Space Complexity

**O(n)**

In the worst case, all opening brackets are stored in the stack.

---

## What I Learned

- How to use a **stack** to solve bracket-matching problems.
- The **Last In, First Out (LIFO)** principle of stacks.
- How to detect unmatched opening and closing brackets.
- Why checking if the stack is empty is important before popping.
- Validating nested and ordered brackets efficiently in a single traversal.

---

**Happy Coding! 🚀**
