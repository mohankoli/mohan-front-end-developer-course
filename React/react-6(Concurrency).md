# Rendering, Concurrency & React 18 — Interview Notes

## 1. What is React Fiber and why was it introduced? (High-level)
React Fiber is a reimplementation of React’s reconciliation algorithm.
It allows React to:
- break rendering work into small units
- pause and resume work
- prioritize updates (high vs low priority)
- improve responsiveness for complex UIs

Fiber enables concurrency by making rendering interruptible.

---

## 2. What is batching and how did it change in React 18?
Batching groups multiple state updates into a single render to avoid unnecessary re-renders.

Before React 18:
- automatic batching only inside React event handlers

After React 18:
- automatic batching across:
  - promises
  - async/await
  - timeouts
  - native event handlers

Example (React 18 batches both):
```js
setTimeout(() => {
  setCount(c => c + 1);
  setFlag(f => !f);
  // renders once instead of twice
});
```

---

## 3. What is concurrent rendering and its benefits?
Concurrent rendering lets React work on UI updates in the background without blocking the main thread.

Benefits:
- smoother UI under heavy updates
- better interrupt handling
- avoids jank
- can prioritize urgent updates (e.g., typing)
- prepares for features like Suspense + streaming

---

## 4. What is useTransition and when do you use it?
`useTransition` lets you mark updates as non-urgent.

Usage example:
```jsx
const [isPending, startTransition] = useTransition();

startTransition(() => {
  setFilteredItems(expensiveFilter(data));
});
```

Use cases:
- filtering/searching large lists
- tab/route transitions
- non-urgent rendering workloads

---

## 5. What is startTransition and how does it improve UX?
`startTransition` schedules state updates at a lower priority.

Example:
```jsx
startTransition(() => {
  setPage('details');
});
```

Benefits:
- keeps input responsive
- prevents UI from freezing
- separates urgent (typing) vs non-urgent (rendering)

---

## 6. Render Phase vs Commit Phase
React rendering has two main phases:

### **Render Phase**
- computes what UI should look like
- can be paused or restarted
- does NOT touch the DOM

### **Commit Phase**
- applies changes to the DOM
- runs effects (`useEffect`, `useLayoutEffect`)
- cannot be interrupted

---

## 7. Why does React StrictMode cause double renders?
In development mode, StrictMode intentionally double-invokes components to:
- detect unsafe side effects
- find non-idempotent logic
- highlight potential bugs

Notes:
- only happens in DEV, not in production
- affects render phase only

---

## TL;DR Summary
- Fiber = interruptible rendering engine
- Batching = groups state updates → fewer renders
- Concurrency = non-blocking rendering for responsive UI
- Transition APIs = prioritize urgent vs non-urgent updates
- Render vs Commit = compute vs apply
- StrictMode double render = side-effect detection in DEV
