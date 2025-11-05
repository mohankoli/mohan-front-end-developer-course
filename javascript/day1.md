1. === vs == in javascript =>
https://www.youtube.com/watch?v=a0S1iG3TgP0&t=18s
2. var vs let vs const differnce => https://www.youtube.com/watch?v=T4QOc53qRp4
### Q.3) What is the Temporal Dead Zone (TDZ) in JavaScript?

👉 The **Temporal Dead Zone** is the time between entering a block and when a `let` or `const` variable is declared, during which accessing the variable causes a **ReferenceError**.

```js
{
  console.log(a); // ReferenceError
  let a = 5;
}
