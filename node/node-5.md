- **What is Redis Cache**
  - **Redis** is an **in-memory data store**.
  - It is commonly used as a **cache**.
  - Data is stored in **RAM**, so it is **very fast**.
  - Used to store **frequently accessed data**.
  - Helps reduce **database load** and **response time**.

- **Why Redis is used as a cache**
  - Faster than database queries.
  - Improves **application performance**.
  - Helps applications **scale**.
  - Supports **key-value** data storage.

- **Common Redis cache use cases**
  - API response caching
  - Session storage
  - User authentication tokens
  - Frequently used lookup data

- **What is Clustering in Node.js**
  - Clustering allows a Node.js app to use **multiple CPU cores**.
  - Node.js normally runs on **a single core**.
  - With clustering, the app creates **multiple worker processes**.
  - Each worker handles **incoming requests**.
  - This improves **performance and scalability**.

- **Why Clustering is used**
  - To handle **high traffic**.
  - To better use **multi-core CPUs**.
  - To avoid one process becoming a **bottleneck**.

- **How Clustering works (Simple)**
  - One **master process**
  - Multiple **worker processes**
  - Requests are distributed among workers
- **What is a Load Balancer (Nginx) with Node.js**
  - A **load balancer** distributes incoming requests across **multiple Node.js servers**.
  - **Nginx** is commonly used as a **load balancer**.
  - It sits **in front of Node.js applications**.
  - Prevents one server from getting **overloaded**.
  - Improves **performance, reliability, and scalability**.

- **Why use Nginx with Node.js**
  - Handles **high traffic** efficiently.
  - Provides **failover** if one Node.js instance goes down.
  - Improves **response time**.
  - Can also handle:
    - **SSL termination**
    - **Static files**
    - **Reverse proxying**

- **Simple request flow**
  ```text
  Client → Nginx (Load Balancer) → Node.js App 1 / App 2 / App 3


