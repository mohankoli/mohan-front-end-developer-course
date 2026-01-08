# React Interview – 2 Core Questions

---

## 1. What is Virtual DOM and what are its trade-offs?

### Virtual DOM

The **Virtual DOM** is a **lightweight JavaScript representation of the real DOM**. React keeps it in memory to track UI changes efficiently.

Instead of updating the real DOM directly, React:

* Updates the Virtual DOM
* Compares it with the previous version
* Applies only the required changes to the real DOM

### Trade-offs

**Advantages ✅**

* Reduces expensive DOM operations
* Improves performance for large UIs
* Enables efficient batch updates

**Disadvantages ❌**

* Extra memory usage
* Diffing has computation cost
* Not always faster for very small apps

---

## 2. How does React update the real DOM efficiently?

### Process

1. State or props change
2. New Virtual DOM is created
3. React compares old and new Virtual DOM (**diffing**)
4. React calculates minimal changes
5. Only changed nodes are updated in the real DOM

This process is called **Reconciliation**.

---

### One-line Interview Answer ⭐

> React uses the Virtual DOM and reconciliation to apply only minimal updates to the real DOM, improving performance.

---
