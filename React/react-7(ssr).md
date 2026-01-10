# SSR, Enterprise Architecture & Stability — Interview Notes

## 1. SSR vs CSR vs ISR vs SSG — How to Choose?
- **CSR (Client-Side Rendering)**: Rendering happens in browser. Best for SPAs, dashboards, low SEO.
- **SSR (Server-Side Rendering)**: Server renders HTML on each request. Good for SEO + dynamic content.
- **SSG (Static Site Generation)**: Build HTML at build time. Ideal for blogs, docs, marketing pages.
- **ISR (Incremental Static Regeneration)**: Rebuild static pages on demand. Perfect for e-commerce, catalogs.

Decision factors:
- SEO needs
- data freshness
- build time constraints
- infrastructure cost
- TTFB performance

---

## 2. What is Server-Side Rendering (SSR)?
Server generates HTML and sends it to browser. Client hydrates after JS loads.

Pros:
- SEO friendly
- Good first paint performance
- Great for content-driven web

Cons:
- Higher server cost
- Hydration overhead in browser
- Latency depends on server

---

## 3. What is Hydration?
Hydration attaches React event listeners and state to server-rendered HTML to make it interactive.

Flow:
1. Server renders HTML
2. Browser loads + displays HTML
3. React hydrates → makes interactive

---

## 4. What is Hydration Mismatch & How to Fix?
Mismatch = server-rendered HTML differs from client-rendered HTML.

Causes:
- random output (Date.now, Math.random)
- browser-only APIs on server (window, localStorage)
- conditional logic differences
- async data not synced

Fixes:
- remove non-deterministic output in render path
- move browser logic to `useEffect`
- share data layer between server + client
- use `suppressHydrationWarning` for harmless diffs

---

## 5. What are React Server Components (High-Level)?
React Server Components:
- run on server
- fetch data server-side
- do not ship JS to browser
- support streaming rendering

Used in Next.js 13+ App Router for performance.

---

## 6. How React Integrates with Next.js in Enterprise Apps
Next.js adds:
- routing system
- SSR / SSG / ISR control
- RSC support
- API routes
- filesystem-based bundling
- CDN + caching
- edge rendering support

Enterprise benefits:
- better SEO
- performance budgets
- global deployments
- improved DX & CI/CD

---

## 7. What is Partial Hydration & Why Important?
Partial hydration hydrates only interactive islands, not the whole HTML.

Benefits:
- huge reduction in JavaScript sent
- faster hydration
- better low-end device performance

Astro popularized **Island Architecture** for partial hydration.

---

## 8. What are Error Boundaries & Where to Place Them?
Error boundaries catch React rendering errors, preventing full app crash.

Good placements:
- around routes
- around heavy widgets
- around async/lazy components
- around boundary of micro-frontends

Principle: **fail small, not global**.

---

## 9. Handling Slow Networks & Error States in React Apps
Real-world techniques:
- skeletons for loading
- Suspense fallbacks
- retries + exponential backoff
- caching (React Query, SWR)
- optimistic updates for UX
- offline mode via Service Workers
- network-aware rendering (`navigator.connection`)

---

## TL;DR Summary
- SSR = server render each request
- SSG = static at build
- ISR = static + refresh on demand
- Hydration = bind React to server HTML
- Partial Hydration = hydrate only interactive parts
- RSC = components executing on server
- Error boundaries = prevent UI from crashing
- Slow network handling = skeletons + caching + retries
