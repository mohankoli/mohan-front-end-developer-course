# Part A -- ReactJS (150 Questions) --- Answers (1--10)

## 1. What is React and why is it popular?

React is a **JavaScript library for building user interfaces**, created
by Facebook (Meta).\
**Why it's popular:** - Component-based architecture\
- Virtual DOM for fast rendering\
- Strong community & ecosystem\
- Easy to integrate with existing apps\
- Supports modern concepts like hooks

## 2. What are components in React?

Components are **reusable UI units** that return JSX.\
Types: - **Functional components** (recommended) - **Class components**
(legacy)

## 3. Difference between class and functional components?

  Feature       Class Components    Functional Components
  ------------- ------------------- -----------------------
  Syntax        ES6 class           JavaScript function
  State         this.state          useState hook
  Lifecycle     lifecycle methods   useEffect hook
  Performance   heavier             lighter
  Usage         old apps            modern apps

## 4. What is JSX and how does it work?

JSX stands for **JavaScript XML**.\
It lets you write HTML-like syntax inside JavaScript.\
JSX is compiled by **Babel** into `React.createElement()` calls.

## 5. What are props in React?

Props are **inputs passed from parent to child components**.\
They are **read-only**.

## 6. What is state and how is it used?

State is **mutable data** managed inside a component.\
State changes trigger UI re-rendering.

## 7. Difference between props and state?

  Props                     State
  ------------------------- --------------------------
  Passed by parent          Managed within component
  Read-only                 Mutable
  Static                    Dynamic
  No re-render on change?   Re-render UI on change

## 8. What are React hooks?

Hooks are **special functions** that allow functional components to have
state and lifecycle features.\
Examples: `useState`, `useEffect`, `useMemo`, `useCallback`.

## 9. Explain useState hook with example.

``` js
const [count, setCount] = useState(0);

<button onClick={() => setCount(count + 1)}>Increase</button>
```

`useState` returns an array → `[stateValue, setStateFunction]`.

## 10. Explain useEffect hook and its dependencies.

`useEffect` is used for **side effects** (API calls, subscriptions,
timers).

``` js
useEffect(() => {
  console.log("Component mounted or updated");
}, [dependency]);
```

-   `[]` → run only once\
-   `[value]` → run when value changes\
-   No dependency → run on every render
