# RxJS – 30 Most Important Interview Questions (with Scenario-Based Questions)

> Targeted for **Senior / Angular / Frontend Engineers**. Includes **theory + real-world scenarios** often asked in interviews.

---

## 🔹 Core RxJS Concepts

### 1. What is RxJS and why is it used in Angular?
**Answer:** RxJS is a reactive programming library for handling async data streams using Observables. Angular uses RxJS for HTTP calls, forms, routing events, and state management.

---

### 2. What is an Observable?
**Answer:**A Subscription is the result of subscribing to an Observable.
It represents the execution of the Observable and gives us control over the async stream.

---

### 3. What is the difference between Observable and Promise?
| Observable | Promise |
|---------|---------|
| Lazy | Eager |
| Multiple values | Single value |
| Can be cancelled | Cannot be cancelled |
| Supports operators | No operators |

---

### 4. What are hot and cold Observables?
**Answer:**
- **Cold:** Starts execution on subscription (HTTP)
- **Hot:** Produces values regardless of subscribers (Subject, events)

---

### 5. What is a Subscription?
**Answer:** A subscription is the execution of an Observable and allows cleanup using `unsubscribe()`.

---

### 6. Why is unsubscribing important?
**Answer:** To prevent **memory leaks**, especially for long-lived streams like `interval`, `fromEvent`.

---

## 🔹 Subjects & Multicasting

### 7. What is a Subject?
**Answer:** A Subject is both an **Observable and an Observer**, enabling multicasting.

---

### 8. Difference between Subject, BehaviorSubject, ReplaySubject, AsyncSubject?
| Type | Behavior |
|----|----|
| Subject | No initial value |
| BehaviorSubject | Emits latest value + initial value |
| ReplaySubject | Replays last N values |
| AsyncSubject | Emits last value on complete |

---

### 9. When would you use BehaviorSubject?
**Answer:** For state management where the latest value is always required (auth user, theme).

---

## 🔹 Operators (Very Important)

### 10. What are RxJS operators?
**Answer:** Pure functions used to transform, filter, or combine streams using `pipe()`.

---

### 11. Difference between `map` and `tap`?
- `map` → transforms data
- `tap` → side effects (logging, analytics)

---

### 12. Difference between `mergeMap`, `switchMap`, `concatMap`, `exhaustMap`?
| Operator | Behavior |
|------|------|
| mergeMap | Parallel, no cancel |
| switchMap | Cancels previous |
| concatMap | Queued, sequential |
| exhaustMap | Ignores new until complete |

---

### 13. When should you use `switchMap`?
**Answer:** Search input, typeahead, route change API calls.

---

### 14. What is `shareReplay` and why is it used?
**Answer:** Caches and shares the latest emission to avoid duplicate API calls.

---

### 15. Difference between `combineLatest` and `forkJoin`?
| combineLatest | forkJoin |
|----|----|
| Emits continuously | Emits once |
| Needs initial emission | Needs completion |

---

## 🔹 Error Handling & Completion

### 16. How do you handle errors in RxJS?
**Answer:** Using `catchError`, `retry`, `retryWhen`.

---

### 17. What happens if an Observable errors out?
**Answer:** Stream terminates and no further emissions occur.

---

### 18. What is `finalize`?
**Answer:** Runs cleanup logic when observable completes or errors.

---

## 🔹 Scenario-Based Questions (🔥 Interview Favorites)

### 19. Scenario: Search box API should cancel previous calls
**Answer:** Use `switchMap` with `debounceTime` and `distinctUntilChanged`.

---

### 20. Scenario: Prevent multiple button clicks until API finishes
**Answer:** Use `exhaustMap`.

---

### 21. Scenario: Execute API calls sequentially
**Answer:** Use `concatMap`.

---

### 22. Scenario: Run multiple APIs in parallel and wait for all
**Answer:** Use `forkJoin`.

---

### 23. Scenario: Cache API response and reuse it
**Answer:** Use `shareReplay(1)`.

---

### 24. Scenario: Retry API call 3 times on failure
**Answer:** Use `retry(3)`.

---

### 25. Scenario: Poll API every 10 seconds
**Answer:** Use `interval` + `switchMap`.

---

### 26. Scenario: Stop Observable on component destroy
**Answer:** Use `takeUntil(destroy$)`.

---

### 27. Scenario: Combine userId and route params to fetch data
**Answer:** Use `combineLatest`.

---

### 28. Scenario: Emit only unique values from stream
**Answer:** Use `distinctUntilChanged`.

---

### 29. Scenario: Handle loader visibility for API calls
**Answer:** Use `tap` + `finalize`.

---

### 30. Scenario: Share auth state across components
**Answer:** Use `BehaviorSubject` in a service.

---

## ✅ Pro Interview Tips
- Prefer **Observable over subscribe inside subscribe**
- Avoid manual subscriptions when possible (use `async` pipe)
- Always justify **operator choice** in interviews

---

📌 *If you want:*
- Code snippets for each scenario
- Advanced RxJS marble diagram questions
- Angular + RxJS real interview questions

Just tell me 👍


