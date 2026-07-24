# Day 2 - Combine Two Tables

### LeetCode Problem

**Problem Number:** 175

**Difficulty:** Easy.

---

## Problem Statement

You are given two tables: **Person** and **Address**.

The `Person` table stores each person's ID, first name, and last name, while the `Address` table stores the city and state for some people.

The task is to display the **first name, last name, city, and state** for every person. If a person doesn't have an address in the `Address` table, return **NULL** for the city and state.

---

## Example

### Input

**Person**

| personId | firstName | lastName |
|----------|-----------|----------|
| 1 | Allen | Wang |
| 2 | Bob | Alice |

**Address**

| addressId | personId | city | state |
|----------|----------|---------------|-----------|
| 1 | 2 | New York City | New York |
| 2 | 3 | Leetcode | California |

### Output

| firstName | lastName | city | state |
|-----------|----------|---------------|-----------|
| Allen | Wang | NULL | NULL |
| Bob | Alice | New York City | New York |

---

## My Approach

Since the problem asks for **every person**, I used a **LEFT JOIN**.

I treated the `Person` table as the main table and joined it with the `Address` table using the `personId` column. If a person's address exists, SQL fetches the corresponding `city` and `state`. If there's no matching address, SQL automatically returns `NULL` for those fields.

This makes `LEFT JOIN` the perfect choice because it keeps all records from the `Person` table while adding matching address details whenever available.

---

## Strategy

- Use the `Person` table as the base table.
- Join the `Address` table using `personId`.
- Use a **LEFT JOIN** to include every person.
- Select only the required columns.
- Return the final result.

---

## Algorithm

1. Select `firstName` and `lastName` from the `Person` table.
2. Select `city` and `state` from the `Address` table.
3. Perform a `LEFT JOIN` on `personId`.
4. Return the required columns.

---

## SQL Solution

```sql
SELECT
    Person.firstName,
    Person.lastName,
    Address.city,
    Address.state
FROM Person
LEFT JOIN Address
ON Person.personId = Address.personId;
```

---

## Time Complexity

**O(n)**

The database scans the required records and performs a single join operation.

---

## Space Complexity

**O(1)**

No extra space is used apart from the result returned by the query.

---

## What I Learned

- How to use `LEFT JOIN` in SQL.
- The difference between `LEFT JOIN` and `INNER JOIN`.
- How SQL handles missing matching records by returning `NULL`.
- Why choosing the correct join operation is important for solving database problems.

---
