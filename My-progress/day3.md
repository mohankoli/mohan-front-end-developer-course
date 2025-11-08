# Day 1 (07-nov-2025) Notes

---

## 1. System Design
- [Tabs-Component -system-design](https://github.com/mohankoli/mohan-front-end-developer-course/blob/main/System-design/Tabs-Component.md)

---

## 2. Coding Questions
1. Count character frequencies in a string (return an object).[Coding] [Easy] [JS]
  - https://github.com/mohankoli/mohan-front-end-developer-course/blob/main/Easy-level-JS-Questions/Frequency-Counter.md
2. Find the first non-repeating character in a string. [Coding] [Easy] [JS]
  -  https://github.com/mohankoli/mohan-front-end-developer-course/blob/main/Easy-level-JS-Questions/find-first-non-repeating-character.md
---

# 🌀 Event Loop — Microtasks vs Macrotasks

## **Event Loop**
JavaScript is single-threaded.  
The **Event Loop** manages async operations by moving callbacks from task queues to the call stack once it’s empty — enabling non-blocking behavior.

---

## **Macrotasks**
Larger async tasks queued for later execution.  
**Examples:** `setTimeout`, `setInterval`, `setImmediate`, `I/O`, `requestAnimationFrame`.

🕓 Executed **after all microtasks**.

---

## **Microtasks**
High-priority async callbacks.  
**Examples:** `Promise.then`, `Promise.catch`, `queueMicrotask`, `process.nextTick`.

⚡ Executed **before macrotasks**, right after the current call stack clears.

---

## **Example**
```javascript
console.log("Start");
setTimeout(() => console.log("Macrotask"), 0);
Promise.resolve().then(() => console.log("Microtask"));
console.log("End");



