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

### 6. Explain 'this' Binding Rules

`this` refers to the object that is executing the current function.  
It’s determined **by how the function is called**, not where it’s defined.


# 🌀 Event Loop — Microtasks vs Macrotasks

## **Event Loop**

The Event Loop keeps checking the call stack.  
When the call stack is empty, it takes tasks from the callback queue and moves them to the call stack for execution.  
This allows JavaScript to handle async tasks without blocking the main thread.


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


#### 1. Default Binding (this keyword example)
When a function is called alone (not as a method):
```js
function show() {
  console.log(this);
}
show(); // In strict mode: undefined; else: window (global)
console.log("End");

