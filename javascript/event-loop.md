# JavaScript Event Loop (Quick Guide)

## What is the Event Loop?
JavaScript is single-threaded → it can do one thing at a time.

So how does JS handle:

setTimeout

Promise

API calls

DOM events

The **event loop** allows JavaScript (single-threaded) to handle asynchronous operations like timers, promises, and events.

It decides **what runs next** when the call stack is empty.

---

## Execution Order
```
Call Stack
→ Microtasks (ALL)
→ One Macrotask
→ Repeat
```

---

## Microtasks (High Priority)
Run immediately after the current code finishes.

**Examples:**
- Promise.then / catch / finally
- queueMicrotask
- MutationObserver

---

## Macrotasks (Low Priority)
Run after microtasks.

**Examples:**
- setTimeout
- setInterval
- setImmediate (Node.js)
- DOM events

---

## Simple Example

```js
console.log("start");

setTimeout(() => {
  console.log("timeout");
}, 0);

Promise.resolve().then(() => {
  console.log("promise");
});

console.log("end");
```

### Output
```
start
end
promise
timeout
```

---

## Key Rule (Interview)
> Microtasks always run before macrotasks.

---

## One-Line Interview Answer
**The event loop executes synchronous code first, then microtasks (Promises), and finally macrotasks (timers/events) to keep JavaScript non-blocking.**
