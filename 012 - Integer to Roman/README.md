````markdown
# Day 12 - Integer to Roman

### LeetCode Problem

**Problem Number:** 12

**Difficulty:** Medium

---

## Problem Statement

Given an integer `num`, convert it into its corresponding **Roman numeral**.

Roman numerals are represented using the following symbols:

| Symbol | Value |
|--------|------:|
| I | 1 |
| V | 5 |
| X | 10 |
| L | 50 |
| C | 100 |
| D | 500 |
| M | 1000 |

Special subtractive combinations are also used:

- IV = 4
- IX = 9
- XL = 40
- XC = 90
- CD = 400
- CM = 900

The input number is guaranteed to be between **1** and **3999**.

---

## Example

### Input

```text
num = 3749
```

### Output

```text
"MMMDCCXLIX"
```

---

### Input

```text
num = 58
```

### Output

```text
"LVIII"
```

---

### Input

```text
num = 1994
```

### Output

```text
"MCMXCIV"
```

---

## My Approach

I solved this problem using a **greedy approach**.

First, I created a dictionary that maps integer values to their corresponding Roman numerals, including the special cases like `IV`, `IX`, `XL`, `XC`, `CD`, and `CM`.

Then, I traversed the values from the largest to the smallest. For each value, I repeatedly checked whether it could be subtracted from the given number.

If it could, I added the corresponding Roman numeral to the result and reduced the number by that value. This process continued until the number became zero.

By always choosing the largest possible Roman numeral first, the final answer follows the correct Roman numeral rules.

---

## Strategy

- Create a lookup dictionary for Roman numeral values.
- Traverse the values from largest to smallest.
- While the current value is less than or equal to the number:
  - Append its Roman numeral to the result.
  - Subtract the value from the number.
- Repeat until the number becomes zero.

---

## Algorithm

1. Create a dictionary containing Roman numeral mappings.
2. Initialize an empty string to store the result.
3. Iterate through Roman numeral values in descending order.
4. While the current value is less than or equal to the number:
   - Append its Roman numeral to the result.
   - Subtract the value from the number.
5. Return the final Roman numeral string.

---

## Python Solution

```python
class Solution:
    def intToRoman(self, num: int) -> str:
        # Creating Dictionary for Lookup
        num_map = {
            1: "I",
            5: "V",    4: "IV",
            10: "X",   9: "IX",
            50: "L",   40: "XL",
            100: "C",  90: "XC",
            500: "D",  400: "CD",
            1000: "M", 900: "CM",
        }

        # Result Variable
        r = ''

        for n in [1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1]:
            while n <= num:
                r += num_map[n]
                num -= n

        return r
```

---

## Time Complexity

**O(1)**

The number of Roman numeral values is fixed, and the input is limited to **3999**, so the algorithm runs in constant time.

---

## Space Complexity

**O(1)**

Only a fixed-size dictionary and a result string are used.

---

## What I Learned

- How the **greedy algorithm** can be used to solve conversion problems.
- Why processing values from largest to smallest guarantees the correct Roman numeral.
- How lookup tables (dictionaries) simplify mapping between values and symbols.
- The importance of handling special subtractive cases like `IV`, `IX`, `XL`, `XC`, `CD`, and `CM`.
- Building the final result by repeatedly reducing the input number.

---

**Happy Coding! 🚀**
````
