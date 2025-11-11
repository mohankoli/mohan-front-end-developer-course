# (11-nov-2025) Notes

---

## 1. System Design
- https://github.com/mohankoli/mohan-front-end-developer-course/blob/main/System-design/Date-Picker.md
---

## 2. Coding Questions
1. Implement Array Flattening in JavaScript. [Coding] [Easy] [JS]
  -  https://github.com/mohankoli/mohan-front-end-developer-course/blob/main/Easy-level-JS-Questions/%20Flatten-Deeply-Nested-Array.md
2. Custom myReduce() Implementation. [Coding] [Easy] [JS]
  - https://github.com/mohankoli/mohan-front-end-developer-course/blob/main/Easy-level-JS-Questions/polyfill-reduce.md

---

## 3.# ✅ 11. Explain **Strict Mode** in JavaScript (with example in a single file)

## ✅ What is Strict Mode?
**Strict Mode** is a special mode in JavaScript that applies stricter rules, helps catch errors early, and prevents unsafe or confusing behaviors.  
You enable it using `"use strict"` at the top of a file or inside a function.

---

## ✅ Why Strict Mode?
- Prevents accidental global variables  
- Converts silent errors into actual errors  
- Disallows duplicate function parameters  
- `this` inside functions becomes `undefined` instead of `window`  
- Prevents deleting variables or functions  
- Helps JS engines optimize code  

---

## 5. What is the Temporal Dead Zone (TDZ) in JavaScript?

👉 The **Temporal Dead Zone** is the time between entering a block and when a `let` or `const` variable is declared, during which accessing the variable causes a **ReferenceError**.

```js
{
  console.log(a); // ReferenceError
  let a = 5;
}



