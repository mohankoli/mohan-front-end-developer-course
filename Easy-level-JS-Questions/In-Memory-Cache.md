# Simple In-Memory Cache With TTL

This example implements a basic cache with TTL (time-to-live) using `setTimeout` to automatically remove keys after expiration.

---

## Code

```js
class Cache {
  constructor() {
    this.store = {};
  }

  set(key, value, time = 3000) {
    this.store[key] = value;
    setTimeout(() => {
      delete this.store[key];
    }, time);
  }

  get(key) {
    return this.store[key];
  }
}

let cache = new Cache();
cache.set('user', { name: 'Mohan' }, 3000);
console.log(cache.get('user'));

setTimeout(() => {
  console.log(cache.get('user'));
}, 3500);
```

---

## Expected Output

```
{ name: 'Mohan' }
undefined
```

---

## Notes

- Cache stores key/value in memory
- TTL auto-expires key using `setTimeout`
- Similar behavior to Redis `SET key value EX seconds`
- Good for interview demonstrations, not production-safe
