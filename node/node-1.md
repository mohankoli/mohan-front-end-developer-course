# Node.js Interview Questions – Set 1

- **What is Node.js?**
  - Node.js is an **open-source**, **cross-platform** JavaScript runtime environment.
  - It executes **JavaScript code outside of a web browser**.
  - Built on the **V8 JavaScript engine**, which compiles JavaScript directly into **machine code**.

- **Difference between `require()` and `import` in Node.js**

| Feature              | `require()`                          | `import`                           |
|----------------------|--------------------------------------|-----------------------------------|
| Module Type          | CommonJS modules                     | ES6 modules                        |
| Usage                | Loads modules at runtime             | Loads modules statically (compile-time) |
| Transpiled Modules   | Not required                          | Can import modules transpiled to ES6 |
| Syntax               | `const module = require('module')`   | `import module from 'module'`     |
| Node.js Support      | Available in all versions             | Available in Node.js 12+ with `"type": "module"` in `package.json` |

- **Explain the Event Loop in Node.js**
  - The Event Loop is a mechanism that allows Node.js to perform **non-blocking I/O operations**.
  - It checks for any **pending tasks in the event queue** and processes them **one by one** in a **single thread**.
  - This makes Node.js **highly scalable**.

- **What are Promises in Node.js**
  - Promises are **objects** that ensure an **asynchronous operation** completes successfully.
  - They are an **alternative to callbacks** for handling asynchronous tasks.
  - Promises work by **chaining `.then()`** for success and **`.catch()`** for errors.
  - Promises also allow **better error handling** and **cleaner code** compared to nested callbacks.

- **What is the purpose of npm in Node.js**
  - **npm (Node Package Manager)** is the default package manager for Node.js.
  - It allows developers to **install, manage, and share packages** of code.
  - Makes it easy to **reuse code** created by other developers.







https://medium.com/@codingguy/top-30-node-js-interview-questions-one-stop-solution-d5cdd80b36ac
