### Q1) What is "undefined" in JavaScript?

👉 A variable with no assigned value is `undefined`.

```js
let a;
console.log(a); // undefined
```

---

### Q2) Output of `undefined == null` and `undefined === null`?

👉 `undefined == null` ➝ `true` (loose equality)  
👉 `undefined === null` ➝ `false` (strict type check)

```js
console.log(undefined == null);  // true  
console.log(undefined === null); // false
```

---

### Q3) Can you assign `undefined` explicitly?

👉 Yes, but not recommended.

```js
let i = undefined;
console.log(i); // undefined
```

---

### Q4) `null` vs `undefined` (1-liner diff)

👉 `null` is intentional empty; `undefined` means uninitialized.

```js
let a = null, b;
console.log(a, b); // null undefined
```



