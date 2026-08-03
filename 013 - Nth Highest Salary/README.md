````markdown
# Day 13 - Nth Highest Salary

### LeetCode Problem

**Problem Number:** 177

**Difficulty:** Medium

---

## Problem Statement

You are given an `Employee` table containing the salaries of employees.

Write a SQL function `getNthHighestSalary(N)` that returns the **Nth highest distinct salary** from the table.

If there are fewer than **N** distinct salaries, the function should return **NULL**.

---

## Example

### Input

**Employee**

| id | salary |
|----|--------|
| 1 | 100 |
| 2 | 200 |
| 3 | 300 |

```text
N = 2
```

### Output

| getNthHighestSalary(2) |
|-------------------------|
| 200 |

---

### Input

**Employee**

| id | salary |
|----|--------|
| 1 | 100 |

```text
N = 2
```

### Output

| getNthHighestSalary(2) |
|-------------------------|
| NULL |

---

## My Approach

The idea is similar to finding the second highest salary, but instead of hardcoding the position, I used the given value of **N**.

Since SQL uses **OFFSET** starting from `0`, I first decreased `N` by `1`.

Next, I selected only **distinct salaries** to avoid duplicate values, sorted them in descending order, and used `LIMIT` with `OFFSET` to retrieve the required salary.

If the requested salary doesn't exist, SQL automatically returns `NULL`, which satisfies the problem requirement.

---

## Strategy

- Convert `N` to zero-based indexing by subtracting `1`.
- Remove duplicate salaries using `DISTINCT`.
- Sort salaries in descending order.
- Use `LIMIT` and `OFFSET` to fetch the Nth highest salary.
- Return the result.

---

## Algorithm

1. Decrease `N` by `1`.
2. Select distinct salaries from the `Employee` table.
3. Sort the salaries in descending order.
4. Skip the first `N` salaries using `OFFSET`.
5. Return the next salary using `LIMIT 1`.
6. If no salary exists, return `NULL`.

---

## SQL Solution

```sql
CREATE FUNCTION getNthHighestSalary(N INT) RETURNS INT
BEGIN
    SET N = N - 1;

    RETURN (
        SELECT DISTINCT salary
        FROM Employee
        ORDER BY salary DESC
        LIMIT 1 OFFSET N
    );
END
```

---

## Time Complexity

**O(n log n)**

The distinct salaries are sorted before retrieving the required position.

---

## Space Complexity

**O(1)**

No extra space is used apart from the query result.

---

## What I Learned

- How to create SQL functions using `CREATE FUNCTION`.
- The difference between one-based and zero-based indexing.
- Using `DISTINCT` to ignore duplicate salaries.
- Retrieving a specific ranked value using `LIMIT` and `OFFSET`.
- SQL automatically returns `NULL` when no matching row exists.

---

**Happy Coding! 🚀**
````
