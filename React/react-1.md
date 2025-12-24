# React Interview Notes (Q1–Q5)

---

## 1. What is React and why is it popular?

**React** is a JavaScript library used to build user interfaces using a **component-based** and **declarative** approach.

### Why React is popular
- Component reusability
- Virtual DOM for efficient UI updates
- One-way data flow (predictable state)
- Strong ecosystem (Next.js, React Query, Redux)
- Large community and long-term support from Meta

**Interview one-liner:**
> React simplifies building fast and scalable UIs by breaking them into reusable components and efficiently updating only what changes.

---

## 2. What are components in React?

Components are **independent, reusable UI blocks** that define how a part of the UI looks and behaves.

### Key points
- Accept inputs via `props`
- Can manage local `state`
- Return JSX
- Improve reusability and testability

### Example
```tsx
function Button({ label }) {
  return <button>{label}</button>;
}
