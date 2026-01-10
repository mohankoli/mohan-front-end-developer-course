# CDN (Content Delivery Network) — Notes

## What is a CDN?
A CDN is a globally distributed network of edge servers that cache and serve content to users with lower latency, higher performance, and reduced load on origin servers.

---

## Why Use CDN?
- Faster page load
- Reduced latency
- Lower origin server load
- High scalability
- DDoS protection
- TLS termination
- Cache efficiency

---

## How CDN Works
1. User requests a resource (e.g., image.js)
2. Edge server checks local cache
3. If cached → return immediately
4. If not cached:
   - Fetch from origin
   - Cache at edge
   - Return to user

---

## Key Components

### Origin Server
Main storage (e.g., S3, App Server)

### Edge / POP
Nearest server delivering cached resources

### Anycast Routing
Routes user to nearest POP

---

## What to Cache via CDN?

| Content | Cache |
|---|---|
| Images | ✅ |
| CSS/JS | ✅ |
| Fonts | ✅ |
| Videos | ✅ |
| HTML | ⚠️ depends |
| Authenticated/private | ❌ |

---

## CDN + Browser Cache Layers
Browser → Edge → Regional → Origin

---

## Cache Control Headers

