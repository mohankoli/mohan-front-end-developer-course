# React Hooks & Advanced Concepts

---

## 1. `useState` Hook
State is data that can change over time in a component.
- Allows functional components to maintain internal state.
- Returns a state value + setter function.
- when state changes components re-renders

**Example:**
```jsx
const [count, setCount] = useState(0);
<button onClick={() => setCount(count + 1)}>+</button>
```

---

## 2. `useEffect` Hook

- useEffect handle side effects.
- Used for fetching data, timers, subscriptions.
- Supports cleanup to avoid memory leaks.
- Dependency array controls execution frequency.
  -  No dependency array → `useEffect` runs after every render.
  - Empty dependency array `[]` → runs only once on mount (on page load).
  - Dependency array with values `[x]` → runs only when `x` changes.
  - Multiple dependencies `[x, y]` → runs when `x` or `y` changes.


**Example:**
```jsx
useEffect(() => {
  document.title = `Count: ${count}`;
  return () => console.log("cleanup");
}, [count]);
```

---

## 20. `useReducer` Hook

- Used when component state logic becomes more complex.
- Uses a reducer function that decides how state should change.
- State changes happen through actions (like commands).
- Similar concept to Redux (state + action + reducer).
- Good when next state depends on previous state.
- Helpful for forms, counters, and multi-step workflows.
- Returns current state and a `dispatch` function to update it.

**Example:**
```jsx
function reducer(state, action) {
  switch (action.type) {
    case 'inc':
      return { count: state.count + 1 };
    default:
      return state;
  }
}

const [state, dispatch] = useReducer(reducer, { count: 0 });
```

---

## 21. `useRef` Hook

- Stores mutable values without causing re-renders.
- Can reference DOM elements.

**Example:**
```jsx
const inputRef = useRef();
<input ref={inputRef} />
```

---

## 22. `useCallback` Hook

- Memoizes callback functions.
- Prevents function recreation on every render.
- Optimizes child components wrapped in `React.memo`.

**Example:**
```jsx
const handleClick = useCallback(() => {
  console.log("clicked");
}, []);
```

---

## 23. `useMemo` Hook

- Memoizes expensive computed values.
- Avoids recalculating on every render.

**Example:**
```jsx
const total = useMemo(() => items.reduce((a, b) => a + b, 0), [items]);
```

---

## 24. Custom Hooks vs `useEffect`

- Custom hooks encapsulate reusable logic.
- Shared logic avoids duplicated effects.
- Helps maintain cleaner component code.

---

## 25. Custom Hook: `useLocalStorage`

**Example:**
```jsx
function useLocalStorage(key, initial) {
  const [value, setValue] = useState(() => JSON.parse(localStorage.getItem(key)) || initial);

  useEffect(() => {
    localStorage.setItem(key, JSON.stringify(value));
  }, [value]);

  return [value, setValue];
}
```

---

## 26. Custom Hook: `useWindowSize`

**Example:**
```jsx
function useWindowSize() {
  const [size, setSize] = useState({ width: window.innerWidth, height: window.innerHeight });

  useEffect(() => {
    const onResize = () => setSize({ width: window.innerWidth, height: window.innerHeight });
    window.addEventListener("resize", onResize);
    return () => window.removeEventListener("resize", onResize);
  }, []);

  return size;
}
```

---

## 27. `React.memo`

- Prevents unnecessary re-renders.
- Works for pure functional components.
- Compares previous props to next props.

**Example:**
```jsx
export default React.memo(Button);
```

---

## 28. React Fiber Architecture

- Reconciliation engine introduced in React 16+.
- Breaks rendering work into small units.
- Enables scheduling, prioritization, pausing.

**Benefits:**
- smoother UI updates
- better performance
- cooperative scheduling

---

## 29. How React Router Works

- Implements client-side routing.
- Uses History API instead of page reloads.
- Maps URL → Component declaratively.

---

## 30. React Portal

- Renders components outside the DOM hierarchy.
- Useful for modals, tooltips, overlays.

**Example:**
```jsx
ReactDOM.createPortal(<Modal />, document.getElementById('portal-root'));
```

---

## 31. `React.lazy` & `Suspense`

- Provides code splitting and lazy loading.
- Improves performance by loading components when needed.

**Example:**
```jsx
const Dashboard = React.lazy(() => import('./Dashboard'));

<Suspense fallback={<Spinner />}>
  <Dashboard />
</Suspense>
```

---

## 32. `useImperativeHandle` Hook

- Controls values exposed via `ref` to parent.
- Used with `forwardRef`.

---

## 33. Higher Order Component (HOC)

- Function that takes a component and returns a new component.
- Enhances component without modifying it directly.

**Example:**
```jsx
const withLogger = Component => props => {
  console.log("Rendered");
  return <Component {...props} />;
};
```

---

## 34. Why React Re-renders

- State change
- Prop change
- Context change
- Parent re-render

---

## 35. Force Re-render Without `setState`

**Example:**
```jsx
const [, forceUpdate] = useReducer(x => x + 1, 0);
```

---

## 36. Server-Side Rendering (SSR)

- HTML is rendered on server before sent to browser.
- Helps SEO + improves performance.
