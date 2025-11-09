# Day 1 (08-nov-2025) Notes

---

## 1. System Design
- [Toast Component Design](https://github.com/mohankoli/mohan-front-end-developer-course/blob/main/System-design/Toast.md)

---

## 2. Coding Questions
1. Custom myMap() Implementation in JavaScript. [Coding] [Easy] [JS]
  -  https://github.com/mohankoli/mohan-front-end-developer-course/blob/main/Easy-level-JS-Questions/polyfill-map.md
2. Custom myFilter() Implementation in JavaScript. [Coding] [Easy] [JS]
  - https://github.com/mohankoli/mohan-front-end-developer-course/blob/main/Easy-level-JS-Questions/polyfill-filter.md

---

## 3. What are prototypes and prototypal inheritance? 
- [Video Reference](https://www.youtube.com/watch?v=a0S1iG3TgP0&t=18s)

---

## 4. higher order function
- # 🧩 Higher Order Function in JavaScript

## 🔹 Definition
A **Higher Order Function (HOF)** is a function that **takes another function as an argument** or **returns a function** as its result.
real Examples are map and reduce
---

## 🧠 Example 1 — Function as Argument
```js
function multiplier(factor) {
  return function(number) {
    return number * factor;
  };
}

const double = multiplier(2);
console.log(double(5)); // 10


