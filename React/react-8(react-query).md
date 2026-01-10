# React Query (TanStack Query) — Short Interview Notes

React Query is useful for caching server API calls on the client side, which helps optimize and reduce unnecessary API requests.

## 1. What Problem Does It Solve?
React Query manages **server state**, which is:
- async
- shared
- cacheable
- needs re-fetching
- can become stale

React itself only manages **local UI state**.

---

## 2. Core Features
- Caching
- Stale‑while‑revalidate
- Background refetching
- Request deduping
- Automatic retries
- Pagination & infinite scroll
- Optimistic updates
- Devtools support

---

## 3. Core APIs
```js
useQuery()     // fetch GET requests
useMutation()  // POST/PUT/DELETE
invalidateQueries() // re-fetch data
setQueryData() // optimistic updates
prefetchQuery() // preload data
```

---

## 4. Basic Example
```js
const { data, isLoading } = useQuery(['users'], fetchUsers);
```

---

## 5. Mutation + Invalidation
```js
const mutation = useMutation(addUser, {
  onSuccess: () => queryClient.invalidateQueries(['users'])
});
```

---

## 6. Stale vs Fresh Model
State lifecycle:
```
fresh → stale → inactive → garbage collected
```

---

## 7. When to Use React Query
Use it for:
✔ server data
✔ caching needed
✔ frequent updates
✔ pagination
✔ optimistic UI

Avoid for:
❌ local UI state (modals, inputs, toggles)

---

## 8. React Query vs Redux (High-Level)
| Feature | React Query | Redux |
|---|---|---|
| Server state | ✔ | ⚠ manual |
| UI state | ⚠ | ✔ |
| Caching | ✔ | ❌ |
| Invalidation | ✔ | ❌ |
| Optimistic updates | ✔ | manual |
| Purpose | data fetching | app global state |

---

## 9. Real App Benefits
- fewer network requests
- smoother UX on reload
- better offline support
- handles slow networks
- reduces boilerplate
- SSR ready (Next.js)

---

## 10. Interview One-Liner
> React Query manages server state with caching, stale‑while‑revalidate, background updates, and mutations, making data fetching fast and reliable without manual state logic.
