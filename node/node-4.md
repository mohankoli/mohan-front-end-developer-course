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
   
- **Are Template Engines Server-Side Rendering (SSR)?**
  - Yes, template engines perform **Server-Side Rendering (SSR)**.
  - HTML is **generated on the server** using data.
  - The final HTML is **sent to the browser**.
  - The browser displays the page **without extra JavaScript rendering**.

- **Template Engine Flow (SSR)**
  - Request comes to server
  - Server fetches data
  - Template engine creates HTML
  - HTML is sent to client

- **Examples**
  - Express + **EJS**
  - Express + **Pug**
  - Express + **Handlebars**


