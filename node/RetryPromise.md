# Simple Retry Logic in Node.js

This example demonstrates retrying a Promise-based function using a `while` loop and `async/await`.

---

## Code

```js
function getUser() {
  let success = Math.random() > 0.7;
  return new Promise((res, rej) => {
    if (success) {
      res({ user: 'Mohan koli' });
    } else {
      rej('network Error');
    }
  });
}

async function retry(fn, attempt) {
  while (attempt > 0) {
    try {
      return await fn();
    } catch (err) {
      attempt--;
      console.log('retry');
      if (attempt === 0) {
        throw err;
      }
    }
  }
}

retry(getUser, 3)
  .then((res) => {
    console.log(res);
  })
  .catch((err) => {
    console.log(err);
  });
```

---

## Possible Output

Success case:
```
retry
retry
{ user: 'Mohan koli' }
```

Failure case:
```
retry
retry
network Error
```

---

## Notes

- Uses `async/await`
- Uses `while` → easy to remember
- Stops retrying on success
- Throws error when all retries fail
