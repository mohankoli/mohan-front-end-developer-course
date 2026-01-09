- **How does Node.js handle asynchronous operations**
  - Node.js uses **callback functions**, **Promises**, and **async/await** to handle asynchronous tasks.
  - These mechanisms allow Node.js to **continue running other code** while waiting for the asynchronous operation to finish.
  - This makes Node.js **non-blocking** and **efficient**
  -  for handling many tasks at the same time.
 
- **What is a Callback Function in Node.js**
  - A **callback function** is a function passed as an **argument** to another function.
  - It is **called** once the **asynchronous operation** has completed.
  - Callbacks allow Node.js to **perform tasks without blocking** the main thread.
  - Commonly used for tasks like **reading files, network requests, or database operations**.

- **What is the use of `process` object in Node.js**
  - The **`process` object** provides information about the **current Node.js process**.
  - Allows operations such as:
    - **Exiting** the process (`process.exit()`).
    - **Sending signals** to the process (`process.kill()`).
    - Accessing **environment variables** (`process.env`).
    - Communicating with the **parent process**.
  - Useful for **monitoring and controlling** the running Node.js application.
 
- **Difference between Synchronous and Asynchronous Functions in Node.js**

| Feature                  | Synchronous Functions              | Asynchronous Functions           |
|---------------------------|----------------------------------|---------------------------------|
| Execution                 | Blocks code until task finishes   | Does not block code             |
| Callback                  | Not needed                        | Uses callback, Promise, or async/await |
| Speed                     | Slower for I/O tasks              | Faster for I/O tasks            |
| Example                   | `fs.readFileSync()`               | `fs.readFile()`                 |
| Thread Behavior           | Runs in main thread and waits     | Runs task in background, main thread continues |

- **What is the `package.json` file in Node.js**
  - `package.json` is a **JSON file** that stores **information (metadata)** about a Node.js project.
  - It contains the **project name and version**.
  - Lists **dependencies and devDependencies** required by the project.
  - Defines **scripts** to run commands like start, build, or test.
  - Helps npm understand **how to install and run** the project.




