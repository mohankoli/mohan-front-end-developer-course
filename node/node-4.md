- **Difference between `fs.readFile` and `fs.createReadStream`**

| Feature            | `fs.readFile`                     | `fs.createReadStream`              |
|--------------------|----------------------------------|------------------------------------|
| Data Reading       | Reads entire file at once         | Reads file in chunks               |
| Memory Usage       | High (loads full file in memory)  | Low (memory efficient)             |
| Speed (Large Files)| Slower                            | Faster                              |
| Suitable For       | Small files                       | Large files                         |
| Type               | Asynchronous function             | Stream-based approach               |

- **Explain Cluster module in Node.js**
  - The **cluster module** allows Node.js applications to use **multiple CPU cores**.
  - It works by creating **child processes (workers)**.
  - Each worker runs on a **separate CPU core**.
  - Helps improve **performance** and **scalability**.
  - Commonly used for handling **high traffic** applications.

- **How can you make a Node.js application scalable**
  - Use **clustering** to run multiple instances on **different CPU cores**.
  - Implement a **load balancer** to distribute incoming requests.
  - Avoid **blocking operations** and use **non-blocking, asynchronous code**.
  - Optimize code by using **efficient algorithms**.
  - Use **caching** (Redis, in-memory cache) to reduce database calls.
  - Optimize **database queries** by:
    - Creating proper **indexes**
    - Monitoring and improving **query performance**
   
- **What is a Template Engine**
  - A template engine helps you **generate HTML dynamically**.
  - It allows you to **embed data into HTML pages**.
  - Instead of writing static HTML, you can pass **variables and logic** to templates.
  - Commonly used in **Node.js with Express.js** to render views.

- **Why Template Engines are used**
  - Avoid repeating HTML code.
  - Separate **business logic** from **UI (HTML)**.
  - Make code **clean and maintainable**.

- **Common Template Engines in Node.js**
  - **EJS**
  - **Pug**
  - **Handlebars**


