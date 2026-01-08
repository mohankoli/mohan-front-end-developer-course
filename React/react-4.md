# React – State, Data & Patterns (Interview Notes)

---

## 1. What is `useReducer` and when do you prefer it over `useState`?

### useReducer

`useReducer` is a React hook used for **complex state logic** where state transitions depend on actions.

### Prefer `useReducer` when:

* State has **multiple sub-values**
* State updates depend on **previous state**
* You want **predictable state transitions**
* Managing complex forms or workflows

### Example

```js
function Counter() {
  const [state, dispatch] = React.useReducer(reducer, { count: 0 });

  return (
    <>
      <h2>Count: {state.count}</h2>
      <button onClick={() => dispatch({ type: "INCREMENT" })}>+</button>
      <button onClick={() => dispatch({ type: "DECREMENT" })}>-</button>
      <button onClick={() => dispatch({ type: "RESET" })}>Reset</button>
    </>
  );
}

function Counter() {
  const [state, dispatch] = React.useReducer(reducer, { count: 0 });

  return (
    <>
      <h2>Count: {state.count}</h2>
      <button onClick={() => dispatch({ type: "INCREMENT" })}>+</button>
      <button onClick={() => dispatch({ type: "DECREMENT" })}>-</button>
      <button onClick={() => dispatch({ type: "RESET" })}>Reset</button>
    </>
  );
}

```

---

## 2. How do you decide between local state and global state?

### Local State

Use when:

* State is used by **single component**
* UI-specific state (modal, input, toggle)

### Global State

Use when:

* State is shared across **multiple screens**
* App-wide concerns (auth, theme, user)

### Rule of Thumb

> Keep state **as close as possible** to where it is used.

---

## 3. Context API vs Redux — how do you decide?

### Context API

* Good for **low-frequency updates**
* Avoids prop drilling
* Simple setup

### Redux

* Best for **large-scale applications**
* Predictable state flow
* Time-travel debugging

### Decision

* Small app → Context API
* Large app with frequent updates → Redux

---

## 4. How do you handle forms at scale in React?

### Recommended Approaches

* Controlled components
* Form libraries (React Hook Form, Formik)
* Validation schemas (Yup / Zod)

### Example (React Hook Form)

```js
const { register, handleSubmit } = useForm();
```

### Why libraries?

* Better performance
* Less re-renders
* Built-in validation

---

## 5. How do you share data between sibling or deeply nested components?

### Options

* Lifting state up
* Context API
* Global state (Redux / Zustand)

### Example (Lifting State)

```js
<Parent>
  <ChildA value={value} />
  <ChildB setValue={setValue} />
</Parent>
```

---

## 6. How do you manage derived state correctly?

### Derived State

State that can be **calculated from existing state or props**.

### Best Practice

* Do NOT store derived state
* Compute it using `useMemo`

### Example

```js
const total = useMemo(() => price * qty, [price, qty]);
```

---

## 7. What are the benefits of immutability in React?

### Benefits

* Enables change detection
* Improves performance
* Predictable updates
* Works well with memoization

### Example

```js
setItems([...items, newItem]); // immutable
```

---

## 8. Common React anti-patterns seen in real projects

### Anti-patterns ❌

* Storing derived state
* Overusing `useEffect`
* Mutating state directly
* Using index as key
* Overusing Context
* Premature optimization

### Good Practice ✅

> Prefer simplicity, predictability, and colocated state.

---

## Interview Tip ⭐

Mention **predictability, performance, and maintainability** in all answers.

---
