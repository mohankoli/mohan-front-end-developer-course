# React Interview – Core Concepts (Simple & Clear)

---

## 1. Difference between useMemo and useCallback

### useMemo

* Used to **memoize a calculated value**
* Avoids re-running expensive calculations

```js
const total = useMemo(() => calculateTotal(items), [items]);
```

### useCallback

* Used to **memoize a function**
* Prevents child re-renders caused by new function references

```js
const handleClick = useCallback(() => {
  setCount(c => c + 1);
}, []);
```

### Key Difference

* `useMemo` → returns a **value**
* `useCallback` → returns a **function`

---

## 2. What is Context API and when should it be used?

### Context API

Context API is used to **share data globally** without passing props through multiple component levels (prop drilling).

### Common Use Cases

* Theme (dark / light)
* Logged-in user info
* Language / locale

### When NOT to use

* Frequently changing state
* Complex state management (use Redux/Zustand instead)

---

## 3. What is lifting state up and when is it required?

### Lifting State Up

Moving state to the **nearest common parent** so multiple child components can access and update it.

### When Required

* Sibling components need the same data
* Data must stay in sync

```js
function Parent() {
  const [value, setValue] = useState(0);
  return (
    <>
      <ChildA value={value} />
      <ChildB setValue={setValue} />
    </>
  );
}
```

---

## 4. What is a custom hook and why would you create one?

### Custom Hook

A custom hook is a **reusable function** that uses React hooks and starts with `use`.

### Example

```js
function useFetch(url) {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch(url).then(res => res.json()).then(setData);
  }, [url]);

  return data;
}
```

### Why create custom hooks?

* Reuse logic
* Cleaner components
* Better separation of concerns

---

## 5. What is reconciliation in React? (High-level)

### Reconciliation

Reconciliation is the process by which React **updates the UI efficiently** when state or props change.

### High-level Steps

1. State or props change
2. New Virtual DOM is created
3. React compares old vs new Virtual DOM (diffing)
4. Only necessary changes are applied to the real DOM

### Why it matters

* Improves performance
* Avoids full DOM re-render

---

## Interview Tip

Keep answers short and clear. Mention **performance, reusability, and optimization** wherever possible.

---
