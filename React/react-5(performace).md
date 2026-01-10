# React Performance & Optimization — Interview Notes

## 1. How do you optimize rendering performance in React?
Rendering optimization focuses on avoiding unnecessary renders and reducing expensive work.
Techniques:
- `React.memo()` for component memoization
- `useMemo()` to memoize expensive calculations
- `useCallback()` to memoize callback functions
- `key` usage for lists
- Avoid anonymous functions inline (in critical paths)
- Virtualization for large lists

---

## 2. How do you optimize overall React application performance?
Holistic techniques:
- Code splitting + lazy loading
- React Suspense
- Image optimization (WebP, responsive images)
- Debouncing & throttling
- Avoiding unnecessary network calls
- Caching data (React Query, SWR)
- Using `useTransition` / `useDeferredValue` (Concurrent features)
- Using CDN + compression (gzip/brotli)
- Reducing bundle size

---

## 3. What is memoization in React? (with use case)
Memoization stores computed values so they are not recalculated unless dependencies change.

Example using `useMemo`:
```jsx
const result = useMemo(() => heavyCompute(data), [data]);
```

Real use case:
- Expensive calculations
- Derived data (filters, sorting)
- Formatting large data sets

---

## 4. How do you prevent unnecessary re-renders?
Key approaches:
- `React.memo()` for functional components
- `useCallback()` for stable function references
- `useMemo()` for stable computed values
- Pure components
- Lifting state carefully (avoid global state)
- Avoid passing new objects/arrays as props
- Zustand/Redux selector usage

Example:
```jsx
const MemoChild = React.memo(Child);
```

---

## 5. How do you handle long lists efficiently in React?
Use **windowing / virtualization** to render only visible items.
Popular libraries:
- `react-window`
- `react-virtualized`
- `react-virtuoso`

Example:
```jsx
import { FixedSizeList as List } from 'react-window';
<List height={400} itemCount={10000} itemSize={35} />
```

---

## 6. What is lazy loading and where do you use it?
Lazy loading delays loading of components/resources until needed.
Used for:
- route-based code splitting
- expensive components
- images (below fold)

Example:
```jsx
const Dashboard = React.lazy(() => import('./Dashboard'));
```

---

## 7. What is code splitting and how do you implement it?
Code splitting breaks bundles to reduce initial load time.
React supports via:
- `React.lazy()`
- `Suspense`
- Webpack dynamic import
- React Router lazy routes

Example:
```jsx
const Page = React.lazy(() => import('./Page'));
```

---

## 8. How have you used React Profiler in real projects?
Profiler helps:
- detect wasted renders
- view render timings
- identify slow components
- optimize reconciliation

Usage:
React DevTools → Profiler tab → record → analyze renders

---

## 9. How does React decide which components to re-render?
React re-renders when:
- state changes
- props change
- parent re-renders
- context value changes

Optimization path:
- shallow comparison
- virtual DOM diffing
- reconciliation algorithm

---

## 10. Additional IMPORTANT Concepts for Interviews
- Bundle size optimization (tree shaking)
- Suspense + concurrent rendering
- Reselect selectors (in Redux)
- React Query caching
- Debounce/Throttle input
- Server-side rendering (Next.js)
- Streaming SSR

---

## TL;DR Summary
- Reduce work (memoization, caching)
- Reduce rendering (memo, callbacks)
- Reduce bytes shipped (code splitting, lazy load)
- Reduce computation (virtualization, derived data)
