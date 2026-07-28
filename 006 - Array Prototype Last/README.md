# Day 6 - Array Prototype Last

### LeetCode Problem

**Problem Number:** 2619

**Difficulty:** Easy

---

## Problem Statement

Write code that extends the JavaScript `Array` object by adding a `last()` method.

The method should:

- Return the last element of the array if it exists.
- Return `-1` if the array is empty.

The array is guaranteed to be a valid JSON array.

---

## Example

### Input

```javascript
nums = [null, {}, 3];
```

### Output

```javascript
3
```

---

### Input

```javascript
nums = [];
```

### Output

```javascript
-1
```

---

## My Approach

I added a new method called `last()` to the `Array` prototype so that it can be used on any array.

First, I checked whether the array is empty by verifying its `length`. If the length is `0`, I returned `-1` as required.

Otherwise, I accessed the last element using `this.length - 1` and returned it.

This approach is simple, efficient, and directly satisfies the problem requirements.

---

## Strategy

- Extend the `Array` prototype by creating a `last()` method.
- Check if the array is empty.
- If empty, return `-1`.
- Otherwise, return the last element using its index.

---

## Algorithm

1. Create a `last()` method on `Array.prototype`.
2. Check whether `this.length` is equal to `0`.
3. If true, return `-1`.
4. Otherwise, return the element at index `this.length - 1`.

---

## JavaScript Solution

```javascript
Array.prototype.last = function() {
    if (this.length === 0) {
        return -1;
    } else {
        return this[this.length - 1];
    }
};
```

---

## Time Complexity

**O(1)**

The method directly accesses the last element of the array without traversing it.

---

## Space Complexity

**O(1)**

No extra space is used.

---

## What I Learned

- How to extend built-in JavaScript objects using `prototype`.
- Using `this` to refer to the current array.
- Accessing the last element with `length - 1`.
- Handling edge cases like empty arrays.
- Writing reusable methods that work for all array objects.

---

**Happy Coding! 🚀**
