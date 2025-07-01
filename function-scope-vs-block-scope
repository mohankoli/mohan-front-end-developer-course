### Q.1) What is hoisting in JavaScript?

👉 Hoisting is JavaScript’s default behavior of **moving declarations to the top** of their scope during compilation.

```js
console.log(a); // undefined
var a = 5;
```

> Only declarations are hoisted (not initializations).  
> `let` and `const` are hoisted but not initialized (temporal dead zone).

---

### Q.2) How does block scope work?

👉 Variables declared with `let` and `const` are **only accessible inside the block `{}`** they’re defined in.

```js
{
  let x = 10;
  console.log(x); // 10
}
console.log(x); // ReferenceError
```

> `var` is **not block scoped**, only function scoped.

---

### Q.3) What is the scope of a variable?

👉 Scope defines **where a variable can be accessed** in your code — it can be **global**, **function**, or **block**.

```js
let a = 1; // global scope

function test() {
  let b = 2; // function scope
  if (true) {
    let c = 3; // block scope
    console.log(c); // 3
  }
}
```

> Always prefer `let`/`const` for block-level scope and better control.
