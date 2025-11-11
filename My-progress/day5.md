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

## 5.# ✅ 12. What Are Arrow Functions? What Is Lexical `this`?

## ✅ What Are Arrow Functions?
**Arrow functions** are a shorter way to write functions in JavaScript.  
They were introduced in ES6 to provide:

- Shorter syntax  
- Lexical (inherited) `this`  
- No own `arguments`, `super`, or `new.target`  
- Cannot be used as constructors

- Arrow functions are best for:
- Callbacks
- Array methods (map/filter)
- Situations where you want to keep `this` from the outer scope


### ✅ Example

const add = (a, b) => a + b;

