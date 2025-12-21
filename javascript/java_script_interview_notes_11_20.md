# JavaScript Interview Questions (11–20)

---

## 11. Explain Strict Mode in JavaScript

**Strict mode** is a special mode in JavaScript that helps you write cleaner and safer code by catching common mistakes.

### How to enable
```js
'use strict';
```

### Benefits
- Prevents use of undeclared variables
- Disallows duplicate parameters
- `this` is `undefined` in functions (not `window`)
- Makes errors visible instead of silent failures

---

## 12. What are Arrow Functions? What is Lexical `this`?

### Arrow Functions
A shorter syntax for writing functions.

```js
const add = (a, b) => a + b;
```

### Lexical `this`
Arrow functions **do not have their own `this`**. They inherit `this` from the surrounding scope.

```js
function Person() {
  this.age = 30;
  setTimeout(() => {
    console.log(this.age); // 30
  }, 1000);
}
```

---

## 13. Difference Between `null` and `undefined`

| Feature | null | undefined |
|------|------|------------|
| Meaning | Intentional empty value | Value not assigned |
| Type | object | undefined |
| Set by | Developer | JavaScript |

```js
let a = null;
let b;
```

---

## 14. What are Pure Functions and Side Effects?

### Pure Function
- Same input → same output
- No side effects

```js
function add(a, b) {
  return a + b;
}
```

### Side Effects
- Modifies external state

```js
let count = 0;
function increment() {
  count++;
}
```

---

## 15. Explain DOM vs BOM

### DOM (Document Object Model)
- Represents HTML structure
- Used to manipulate UI

```js
document.getElementById('id');
```

### BOM (Browser Object Model)
- Interacts with browser features

```js
window.location.href;
navigator.userAgent;
```

---

## 16. How Does Event Delegation Work?

Event delegation uses **event bubbling** to handle events at a parent level.

```js
document.getElementById('list').addEventListener('click', (e) => {
  if (e.target.tagName === 'LI') {
    console.log(e.target.textContent);
  }
});
```

### Benefits
- Better performance
- Works for dynamic elements

---

## 17. Bubbling vs Capturing in Events

### Bubbling (default)
- Event flows **child → parent**

### Capturing
- Event flows **parent → child**

```js
element.addEventListener('click', handler, true); // capturing
```

---

## 18. What is CORS? How to Handle It on the Frontend?

**CORS (Cross-Origin Resource Sharing)** allows or blocks API requests between different domains.

### Frontend Handling
- Use correct API URL
- Send credentials if required
- Handle errors properly

```js
fetch(url, { credentials: 'include' });
```

⚠️ **CORS must be fixed on the backend**, not frontend.

---

## 19. HTTP Methods and Status Codes

### HTTP Methods
- **GET** – Fetch data
- **POST** – Create data
- **PUT** – Update full resource
- **PATCH** – Update partial resource
- **DELETE** – Remove data

### Status Codes
| Code | Meaning |
|----|--------|
| 200 | OK |
| 201 | Created |
| 204 | No Content |
| 301 | Moved Permanently |
| 304 | Not Modified |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 500 | Server Error |

---

## 20. localStorage vs sessionStorage vs Cookies

| Feature | localStorage | sessionStorage | Cookies |
|------|-------------|----------------|---------|
| Size | ~5MB | ~5MB | ~4KB |
| Expiry | Never | Tab closed | Configurable |
| Sent to Server | ❌ No | ❌ No | ✅ Yes |
| Use Case | Persist data | Temp data | Auth/session |

```js
localStorage.setItem('key', 'value');
```

---

✅ **Interview Tip:** Focus on real-world usage + small examples.

