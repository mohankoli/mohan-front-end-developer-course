# (10-nov-2025) Notes

---

## 1. System Design
- 

---

## 2. Coding Questions
1. Implement Array Flattening in JavaScript. [Coding] [Easy] [JS]
  -  https://github.com/mohankoli/mohan-front-end-developer-course/blob/main/Easy-level-JS-Questions/%20Flatten-Deeply-Nested-Array.md
2. Custom myReduce() Implementation. [Coding] [Easy] [JS]
  - https://github.com/mohankoli/mohan-front-end-developer-course/blob/main/Easy-level-JS-Questions/polyfill-reduce.md

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



