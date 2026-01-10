# Helmet.js with Express — Interview Notes

## 1. What is Helmet.js?
Helmet.js is an Express middleware that sets secure HTTP headers to protect web applications from common web vulnerabilities like XSS, clickjacking, MIME sniffing, and other header-based attacks.

## 2. Why is Helmet used?
Reasons:
- Improves security using HTTP headers
- Mitigates common web attacks
- Enforces secure browser policies
- Recommended for production environments

## 3. Installation & Basic Usage
```bash
npm install helmet
```
```js
import express from "express";
import helmet from "helmet";

const app = express();
app.use(helmet());
```

## 4. Security Threats Helmet Helps Mitigate
| Threat | Explanation |
|---|---|
| XSS | Prevents malicious script execution |
| Clickjacking | Prevents UI being loaded in iframes |
| MIME Sniffing | Prevents browsers guessing MIME types |
| HTTPS Downgrade | Enforces HTTPS using HSTS |
| Info Leakage | Hides sensitive server details |

## 5. Important Helmet Modules (Modern)
| Module | Purpose |
|---|---|
| contentSecurityPolicy | Prevents XSS/script injections |
| frameguard | Prevents clickjacking |
| hsts | Forces HTTPS |
| noSniff | Prevents MIME sniffing |
| referrerPolicy | Controls referrer metadata |
| crossOriginResourcePolicy | Controls resource sharing across origins |
| crossOriginEmbedderPolicy | Enables secure cross-origin isolation |

## 6. Example with Configured Policies
```js
app.use(helmet({
  contentSecurityPolicy: {
    directives: {
      defaultSrc: ["'self'"],
      scriptSrc: ["'self'", "https://cdn.jsdelivr.net"],
      imgSrc: ["'self'", "data:"],
    },
  },
  referrerPolicy: { policy: "no-referrer" },
}));
```

## 7. Content-Security-Policy (CSP)
CSP is the most important policy preventing XSS by restricting which scripts/styles/images can load.

Example:
```
Content-Security-Policy: default-src 'self'; script-src 'self' cdn.jsdelivr.net;
```

## 8. Production Usage
Typical deployment:
Client → CDN → NGINX → Express → Helmet

## 9. When Helmet May Break Apps
Helmet can block:
- Inline scripts
- Third-party CDNs (analytics, fonts)
- iframes
- Embeds (YouTube, Maps)

Fix: whitelist via CSP directives.

## 10. Helmet Does NOT Protect Against
Not for:
- SQL Injection
- CSRF
- Authentication issues
- Business logic issues
- Rate limiting abuse

Helmet is part of a security stack, not full security.

## 11. Complementary Libraries
| Concern | Solution |
|---|---|
| CSRF | csurf |
| Rate-limiting | express-rate-limit |
| Sanitization | validator / sanitize-html |
| CORS | cors |

## 12. Recommended Production Setup
```js
import rateLimit from "express-rate-limit";
import helmet from "helmet";
import cors from "cors";

app.use(helmet());
app.use(cors());
app.use(rateLimit({ windowMs: 15 * 60 * 1000, max: 200 }));
```

## 13. Real Interview Questions
1. What is Helmet.js and why is it used?
2. Which attacks does Helmet mitigate?
3. What is CSP and why is it important?
4. Difference between CORS and CSP?
5. Can Helmet break UI? Why?
6. Does Helmet secure backend fully? Why not?
7. Which other middleware should be used with Helmet?
8. How to secure Express in production?

## 14. Key Takeaways
- Helmet sets security headers
- Helps mitigate client-side attack vectors
- CSP is critical for XSS prevention
- Needs combination with auth, CSRF, sanitization & rate limiting
- Recommended for production deployments
