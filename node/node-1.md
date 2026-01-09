# Node.js Interview Questions – Set 1

## N1. Is Node.js single-threaded? How does it handle concurrency?
Node.js runs on a single-threaded event loop, but it handles concurrency using non-blocking I/O operations.
Time-consuming tasks are offloaded to the libuv thread pool, allowing Node.js to handle many requests efficiently.

---

## N2. Explain the Event Loop in Node.js.
The event loop allows Node.js to execute asynchronous callbacks using a single thread.
It is responsible for handling timers, I/O operations, and promise callbacks without blocking execution.

---

## N3. Blocking vs Non-blocking operations.
Blocking operations halt the execution of the event loop until the task completes.
Non-blocking operations allow the event loop to continue processing other requests while waiting for results.

---

## N4. Difference between `process.nextTick()` and `setImmediate()`.
`process.nextTick()` executes callbacks before the next event loop iteration.
`setImmediate()` executes callbacks in the check phase of the event loop.

---

## N5. How does `async/await` work internally?
`async/await` is syntactic sugar built on top of Promises.
It uses the microtask queue to handle asynchronous execution in a synchronous-looking manner.
