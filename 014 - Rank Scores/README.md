````markdown id="y8qk41"
# Day 14 - Rank Scores

### LeetCode Problem

**Problem Number:** 178

**Difficulty:** Medium

---

## Problem Statement

You are given a `Scores` table that contains the score achieved by each player.

Your task is to assign a **rank** to every score based on the following rules:

- Higher scores receive a better rank.
- Equal scores receive the same rank.
- Rankings should be **dense**, meaning there are no gaps after ties.

Return the result ordered by score in **descending order**.

---

## Example

### Input

| id | score |
|----|-------|
| 1 | 3.50 |
| 2 | 3.65 |
| 3 | 4.00 |
| 4 | 3.85 |
| 5 | 4.00 |
| 6 | 3.65 |

### Output

| score | rank |
|-------|------|
| 4.00 | 1 |
| 4.00 | 1 |
| 3.85 | 2 |
| 3.65 | 3 |
| 3.65 | 3 |
| 3.50 | 4 |

---

## My Approach

Instead of using built-in ranking functions, I solved this problem by counting the number of **distinct scores** that are greater than or equal to each score.

First, I created a subquery containing only the distinct scores. Then, for every score in the original table, I counted how many distinct scores were greater than or equal to it.

This count directly represents the **dense rank** of that score. Finally, I grouped the results by employee ID and sorted them in descending order of score.

---

## Strategy

- Get all distinct scores.
- Compare each score with every distinct score.
- Count the number of distinct scores greater than or equal to the current score.
- Use this count as the rank.
- Sort the final result in descending order.

---

## Algorithm

1. Create a subquery containing distinct scores.
2. Compare each score with the distinct scores.
3. Count how many distinct scores are greater than or equal to the current score.
4. Assign the count as the rank.
5. Group the results by ID.
6. Order the output by score in descending order.

---

## SQL Solution

```sql
SELECT
    S.score,
    COUNT(S2.score) AS `rank`
FROM Scores S,
     (SELECT DISTINCT score FROM Scores) S2
WHERE S.score <= S2.score
GROUP BY S.id
ORDER BY S.score DESC;
```

---

## Time Complexity

**O(n²)**

Each score is compared with the set of distinct scores to determine its rank.

---

## Space Complexity

**O(n)**

The subquery stores the distinct scores used for ranking.

---

## What I Learned

- How to calculate **dense ranking** without using SQL window functions.
- Using `DISTINCT` to remove duplicate scores before ranking.
- Counting values with `COUNT()` to generate ranks.
- Using subqueries to simplify ranking problems.
- The difference between **dense rank** and standard ranking.

---

**Happy Coding! 🚀**
````
