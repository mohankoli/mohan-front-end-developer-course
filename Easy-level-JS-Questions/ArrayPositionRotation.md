# Rotate an Array by K Positions (Right Rotation) – JavaScript

## Problem

Rotate an array to the **right** by `k` positions.

---

## Example

```js
Input:  [1, 2, 3, 4, 5]
K:      2
Output: [4, 5, 1, 2, 3]
```

---

## Simple & Recommended Solution

```js
function rotateRight(arr, k) {
  k = k % arr.length; // handle large k
  return arr.slice(-k).concat(arr.slice(0, -k));
}
```

---

## Usage

```js
rotateRight([1, 2, 3, 4, 5], 2);
```

**Output**

```js
[4, 5, 1, 2, 3]
```

---

## Explanation

* `k % arr.length` avoids extra rotations
* `slice(-k)` gets last `k` elements
* `slice(0, -k)` gets remaining elements
* `concat()` joins them

---

## Time & Space Complexity

* Time: **O(n)**
* Space: **O(n)**

---

## One‑Line Interview Explanation

> “I split the array into two parts using slice and join them in rotated order.”

---

## Notes

* This does **not modify** the original array
* Very clean and interview‑friendly solution
