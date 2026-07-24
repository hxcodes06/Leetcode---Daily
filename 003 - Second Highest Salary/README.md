# Day 3 - Second Highest Salary

### LeetCode Problem

**Problem Number:** 176

**Difficulty:** Easy

---

## Problem Statement

You are given an `Employee` table that contains the salary of each employee.

Your task is to find the **second highest distinct salary**. If a second highest salary doesn't exist, return **NULL**.

---

## Example

### Input

| id | salary |
|----|--------|
| 1 | 100 |
| 2 | 200 |
| 3 | 300 |

### Output

| SecondHighestSalary |
|---------------------|
| 200 |

---

### Input

| id | salary |
|----|--------|
| 1 | 100 |

### Output

| SecondHighestSalary |
|---------------------|
| NULL |

---

## My Approach

Instead of comparing every salary manually, I first removed duplicate salaries using `DISTINCT`.

Then, I sorted the salaries in descending order so that the highest salary appears first. Using `LIMIT` and `OFFSET`, I skipped the highest salary and selected the next one, which represents the second highest distinct salary.

To handle the case where a second highest salary doesn't exist, I wrapped the query inside a subquery. If no value is found, SQL automatically returns `NULL`, matching the problem requirement.

---

## Strategy

- Remove duplicate salaries using `DISTINCT`.
- Sort the salaries in descending order.
- Skip the highest salary using `OFFSET 1`.
- Fetch the next salary using `LIMIT 1`.
- Return the result as `SecondHighestSalary`.

---

## Algorithm

1. Select distinct salaries from the `Employee` table.
2. Sort the salaries in descending order.
3. Skip the first (highest) salary.
4. Retrieve the next salary.
5. Return it as `SecondHighestSalary`.
6. If no second highest salary exists, return `NULL`.

---

## SQL Solution

```sql
SELECT (
    SELECT DISTINCT salary
    FROM Employee
    ORDER BY salary DESC
    LIMIT 1 OFFSET 1
) AS SecondHighestSalary;
```

---

## Time Complexity

**O(n log n)**

The query sorts the distinct salary values, which dominates the overall time complexity.

---

## Space Complexity

**O(1)**

No additional data structures are used apart from the query result.

---

## What I Learned

- How to remove duplicate values using `DISTINCT`.
- How `ORDER BY DESC` helps rank values from highest to lowest.
- Using `LIMIT` and `OFFSET` to retrieve specific rows.
- How subqueries can be used to return a single value.
- SQL automatically returns `NULL` when the subquery produces no result, making it easy to handle edge cases.

---

