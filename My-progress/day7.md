# Day 7 (12-nov-2025) Notes

---

## 1. System Design
- [Modal Component Design](https://github.com/mohankoli/mohan-front-end-developer-course/blob/main/System-design/Modal-Component-Design.md)

---

## 2. Coding Questions
1. Remove duplicates from an array while preserving order. [Coding] [Easy] [JS]. [Coding] [Easy] [JS]
  -  https://github.com/mohankoli/mohan-front-end-developer-course/blob/main/Easy-level-JS-Questions/removeDuplicate.md
2. Merge two sorted arrays into a single sorted array. [Coding] [Easy] [JS]
  - https://github.com/mohankoli/mohan-front-end-developer-course/blob/main/Easy-level-JS-Questions/Reverse.md

---

## 3. `===` vs `==` in JavaScript
- [Video Reference](https://www.youtube.com/watch?v=a0S1iG3TgP0&t=18s)

---

## 4. `var` vs `let` vs `const` Difference
- [Video Reference](https://www.youtube.com/watch?v=T4QOc53qRp4)

---

## 5. What is the Temporal Dead Zone (TDZ) in JavaScript?

👉 The **Temporal Dead Zone** is the time between entering a block and when a `let` or `const` variable is declared, during which accessing the variable causes a **ReferenceError**.

```js
{
  console.log(a); // ReferenceError
  let a = 5;
}





