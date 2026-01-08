# React Interview Notes (Core Concepts with Examples)

---

## 1. What is React and why is it popular?

### What is React?

React is an **open-source JavaScript library** developed by **Meta (Facebook)** for building **user interfaces**, especially **single-page applications (SPAs)**.
It focuses on the **view layer** of the application.

### Key Features

* **Component-based architecture**
* **Virtual DOM** for fast rendering
* **Declarative UI**
* **Unidirectional data flow**
* Strong ecosystem (Redux, React Query, Next.js, etc.)

### Why is React popular?

* ⚡ High performance due to Virtual DOM
* 🧩 Reusable components → faster development
* 📦 Huge community and ecosystem
* 💼 Widely used in production (Meta, Netflix, Airbnb)
* 🔁 Easy to manage state with hooks

---

## 2. Difference between Functional and Class Components

### (Why hooks replaced classes?)

| Feature           | Class Component  | Functional Component |
| ----------------- | ---------------- | -------------------- |
| Syntax            | ES6 Classes      | JavaScript Functions |
| State             | `this.state`     | `useState`           |
| Lifecycle methods | Yes              | Via Hooks            |
| `this` keyword    | Required         | Not required         |
| Code size         | More boilerplate | Cleaner & shorter    |
| Reusability       | Limited          | High (custom hooks)  |
| Performance       | Slightly heavier | Lightweight          |

### Class Component Example

```js
class Counter extends React.Component {
  state = { count: 0 };

  componentDidMount() {
    console.log("Mounted");
  }

  render() {
    return <button onClick={() => this.setState({ count: this.state.count + 1 })}>
      {this.state.count}
    </button>;
  }
}
```

### Functional Component with Hooks

```js
function Counter() {
  const [count, setCount] = React.useState(0);

  React.useEffect(() => {
    console.log("Mounted");
  }, []);

  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

### Why Hooks replaced classes?

* ❌ Classes were hard to understand (`this`, binding)
* ❌ Lifecycle logic was scattered
* ❌ Hard to reuse logic between components
* ✅ Hooks enable **logic reuse**
* ✅ Cleaner and more readable code
* ✅ Better abstraction using custom hooks

---

## 3. What are React Hooks and why were they introduced?

### What are Hooks?

Hooks are **functions that let you use React features** (state, lifecycle, context) in **functional components**.

### Common Hooks

* `useState`
* `useEffect`
* `useContext`
* `useMemo`
* `useCallback`
* `useRef`

### Why Hooks were introduced?

* To **remove class components**
* To **reuse stateful logic**
* To **simplify lifecycle handling**
* To make React code **more functional and predictable**

### Example: useState

```js
const [name, setName] = useState("Mohan");
```

---

## 4. Explain `useEffect` with real-world use cases and common pitfalls

### What is useEffect?

`useEffect` is used to handle **side effects** in React such as:

* API calls
* Subscriptions
* Timers
* DOM updates

### Syntax

```js
useEffect(() => {
  // side effect
  return () => {
    // cleanup
  };
}, [dependencies]);
```

---

### Real-world Use Cases

#### 1️⃣ API Call on Component Mount

```js
useEffect(() => {
  fetch("/api/users")
    .then(res => res.json())
    .then(data => setUsers(data));
}, []);
```

#### 2️⃣ Event Listener

```js
useEffect(() => {
  window.addEventListener("resize", handleResize);
  return () => window.removeEventListener("resize", handleResize);
}, []);
```

#### 3️⃣ Dependent Effect

```js
useEffect(() => {
  calculatePrice(quantity);
}, [quantity]);
```

---

### Common Pitfalls

❌ Missing dependency array
→ Causes infinite re-renders

❌ Wrong dependencies
→ Stale values or unexpected behavior

❌ API calls without cleanup
→ Memory leaks

❌ Overusing useEffect
→ Sometimes logic belongs in event handlers

---

## 5. What is `React.memo` and when should you NOT use it?

### What is React.memo?

`React.memo` is a **higher-order component** that **memoizes a component**
→ Prevents re-render **if props don’t change**

### Example

```js
const Child = React.memo(({ value }) => {
  console.log("Rendered");
  return <div>{value}</div>;
});
```

---

### When to use React.memo?

✅ Component renders frequently
✅ Props are primitive values
✅ Component is heavy (charts, lists)
✅ Parent re-renders often

---

### When NOT to use React.memo?

❌ Props are objects/functions (change reference every render)
❌ Component is simple/lightweight
❌ Premature optimization
❌ Adds comparison overhead

### Bad Example

```js
<Child user={{ name: "Mohan" }} /> // new object each render
```

### Better Approach

```js
const user = useMemo(() => ({ name: "Mohan" }), []);
<Child user={user} />
```

---

## Interview Tips

* Hooks **did not remove lifecycle**, they **replaced them**
* `useEffect` combines `componentDidMount`, `componentDidUpdate`, `componentWillUnmount`
* Optimization tools (`memo`, `useMemo`) should be used **carefully**
* Prefer **readability over premature optimization**

---
