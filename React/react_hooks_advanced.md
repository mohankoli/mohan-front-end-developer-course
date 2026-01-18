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

## 3. `useReducer` Hook

- Used when component state logic becomes more complex.
- The reducer holds the business logic and decides how state changes based on actions.
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

## 4. `useRef` Hook

- `useRef` stores values that do not trigger re-renders when changed.
- It can point to DOM elements (like input, div, etc.).
- Useful for accessing or controlling DOM without query selectors.
- Can hold previous values between renders.
- Ref value stays the same across re-renders.
- Updates to `.current` do not refresh the UI.


**Example:**
```jsx
const inputRef = useRef();
<input ref={inputRef} />
```

---

## 5. `useCallback` Hook

- `useCallback` memoizes (remembers) a function between renders.
- It prevents the function from being recreated on every re-render.
- Useful when passing functions to child components that use `React.memo`.
- Helps avoid unnecessary re-renders in child components.
- Takes a dependency array to decide when to recreate the function.
- Returns the same function reference until dependencies change.
- Mainly used for performance optimization in large component trees.
- Good for event handlers (click, input, submit) passed down as props.

when to use it
- When passing functions to memoized children
- When avoiding unnecessary re-renders
- When optimizing performance in large lists or trees


**Example:**
```jsx
const handleClick = useCallback(() => {
  console.log("clicked");
}, []);
```

---

## 6. `useMemo` Hook

- `useMemo` memoizes expensive computed values.
- It avoids recalculating those values on every render.
- Use it when a calculation is heavy or depends on large data.
- Use it if recalculation would hurt performance.
- Common with sorting, filtering, and derived values.


**Example:**
```jsx
const total = useMemo(() => items.reduce((a, b) => a + b, 0), [items]);
```

---
## 7. Custom Hooks

- Custom hooks let you reuse logic across components.
- They prevent writing the same `useEffect` or state code repeatedly.
- They keep components cleaner and easier to read.
- They move logic out of UI and into reusable functions.
- Custom hooks always start with the word `use`.
- They can use other hooks inside (e.g., useState, useEffect, etc.).
- Useful for things like API calls, timers, localStorage, and window events.


**Example: `useFetch` Custom Hook**
```jsx
function useFetch(url) {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch(url)
      .then(res => res.json())
      .then(json => setData(json));
  }, [url]);

  return data;
}
```

---

## 8. Custom Hook: `useLocalStorage`

**Example:**
```jsx
function useLocalStorage(key, initial) {
  const [value, setValue] = useState(() => JSON.parse(localStorage.getItem(key)) || initial);

  useEffect(() => {
    localStorage.setItem(key, JSON.stringify(value));
  }, [value]);

  return [value, setValue];
}

function App() {
  const [name, setName] = useLocalStorage("username", "");

  return (
    <div>
      <input
        value={name}
        onChange={(e) => setName(e.target.value)}
        placeholder="Enter name..."
      />

      <p>Stored Name: {name}</p>
    </div>
  );
}

```

---

## 9. `React.memo`
React.memo is a higher-order component that memoizes a component → Prevents re-render if props don’t change

- `React.memo` prevents unnecessary re-renders.
- Works for pure functional components.
- Compares previous props to next props and re-renders only if changed.
- Useful when component receives the same props repeatedly.
- Use it when child renders are expensive (lists, tables, charts).
- Use it when passing functions via props along with `useCallback`.
- Avoid if props change often (no performance gain).


**Example:**
```jsx
export default React.memo(Button);
```

---

## 10. React Fiber Architecture

React Fiber is a reimplementation of React’s reconciliation algorithm.
It allows React to:
- break rendering work into small units
- pause and resume work
- prioritize updates (high vs low priority)
- improve responsiveness for complex UIs

Fiber enables concurrency by making rendering interruptible.

**Benefits:**
- smoother UI updates
- better performance
- cooperative scheduling

---

## 11. How React Router Works

- React Router enables **client-side routing** in a Single Page Application (SPA).
- It maps URLs to components without doing a full page reload.
- Uses the browser History API (`pushState`, `replaceState`) to update the URL.
- React switches components in memory, keeping the UI fast and seamless.
- Helps maintain deep linking, navigation, and browser back/forward support.

**Example:**
```jsx
import { BrowserRouter, Routes, Route } from "react-router-dom";

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/users" element={<Users />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}
```



---

## 12. React Portal

- Renders components outside the DOM hierarchy.
- Useful for modals, tooltips, overlays.

**Example:**
```jsx
ReactDOM.createPortal(<Modal />, document.getElementById('portal-root'));
```

---

## 13. `React.lazy` & `Suspense`

- `React.lazy` loads a component only when it is needed.
- `Suspense` shows a fallback (like a loader) while waiting.
- Helps reduce the initial bundle size of the app.
- Improves performance and page load time, especially in SPAs.
- Good for large pages, routes, dashboards, or rarely visited screens.

**Example:**
```jsx
const Dashboard = React.lazy(() => import('./Dashboard'));

<Suspense fallback={<Spinner />}>
  <Dashboard />
</Suspense>
```

---

## 14. `useImperativeHandle` Hook

- It allows a child component to decide what functions or values the parent can access through a ref.
- It gives the child control over what is exposed to the parent.
- It is used together with `forwardRef`.
- Parent can call functions on the child (imperative style).

---

## 15. Higher Order Component (HOC)

- A Higher Order Component (HOC) is a function that takes a component and returns a new component.
- It adds extra features or behavior without changing the original component directly.
- Allows reusing logic across multiple components.
- Commonly used for cross-cutting concerns like logging, authorization, fetching, or theming.
- Follows the pattern: `const Enhanced = withSomething(Component)`.


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
