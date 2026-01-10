# Auth Methods — Interview Short Notes

## 1. Basic Auth
- Sends username:password in `Authorization: Basic <base64>` header
- Base64 = encoding, not encryption
- Needs HTTPS for security
- No token, no expiry, no refresh
- Simple for internal APIs

Use cases: internal tools, test APIs

---

## 2. JWT (JSON Web Token)
- Token format for **authorization**
- Structure: `header.payload.signature`
- Contains claims (e.g., sub, role, exp)
- Stateless, no DB lookup
- Hard to revoke
- Needs refresh token strategy

Use cases: SPAs (React/Angular), mobile, microservices

---

## 3. OAuth 2.0
- **Delegated authorization framework**
- Used for “Login with Google” style
- Issues: **access token** + (optional) **refresh token**
- Flows:
  - Auth Code (secure, web apps)
  - PKCE (mobile/SPAs)
  - Client Credentials (machine → machine)
  - Implicit (deprecated)

Use cases: third‑party access, multi‑tenant SaaS

---

## 4. OpenID Connect (OIDC)
- OAuth + Authentication layer
- Provides **ID Token (JWT)**
- Used for Single Sign‑On

---

## 5. Token Types
- **Access Token:** short-lived, used to call APIs
- **Refresh Token:** long-lived, used to get new access tokens

---

## 6. Where to Store Tokens
- Best: HttpOnly + Secure + SameSite cookies
- Avoid: localStorage (XSS risk)

---

## 7. Session vs JWT
| Feature | Session | JWT |
|---|---|---|
| State | Server | Client |
| Revocation | Easy | Hard |
| Scale | Poor | Good |
| Use | Web | Web + Mobile + APIs |

---

## 8. Other Auth Methods
- **API Keys:** identify calling app, not user
- **mTLS:** machine → machine trust
- **Basic Auth:** simple, no expiry

---

## 9. Threats & Risks
- XSS → steals JWT in storage
- CSRF → abuses cookies & refresh tokens
- Token theft → replay attacks
- Consent phishing → OAuth login

---

## 10. Interview Must‑Know Qs
1. OAuth vs OIDC
2. OAuth: Auth or AuthZ?
3. Why refresh tokens?
4. Why PKCE?
5. JWT storage strategy?
6. How to revoke JWT?
7. Session vs JWT?
8. Access vs Refresh Token?
9. Where OAuth fits in system design?
10. Why implicit flow deprecated?

---

## 11. TL;DR
- **Basic Auth:** simple, sends creds every request
- **JWT:** stateless authorization token
- **OAuth:** delegated authorization w/ tokens
- **OIDC:** authentication on top of OAuth
- **Refresh token:** long-lived renewal
- **Session vs JWT:** trade-offs for scale
