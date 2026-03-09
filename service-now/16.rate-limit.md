# Simple Rate Limiting Example in JavaScript

This example demonstrates a basic in-memory rate limiter using a counter and `setTimeout` to reset counts after a 1-minute window.

---

## Code

```js
let store = {};
let limit = 5;

const rateLimit = (ip) => {
  if (!store[ip]) {
    store[ip] = 1;
    setTimeout(() => {
      delete store[ip];
    }, 60000); // reset after 1 minute
  } else {
    store[ip]++;
  }

  if (store[ip] <= limit) {
    console.log(store[ip], " allowed");
  } else {
    console.log(store[ip], " blocked");
  }
};

for (let i = 0; i < 8; i++) {
  rateLimit('127.0.0.1');
}
```

---

## Output Example

```
1 allowed
2 allowed
3 allowed
4 allowed
5 allowed
6 blocked
7 blocked
8 blocked
```

---

## Key Notes

- Stores IP as key and request count as value
- Allows up to **5 requests per minute**
- Uses `setTimeout` to clear stored counts
- Good for learning & interview demonstration, not production-grade
