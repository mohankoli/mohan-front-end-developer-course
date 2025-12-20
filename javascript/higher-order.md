## 8. What is a Higher-Order Function?

A **higher-order function** is a function that does **at least one** of the following:

- Takes another function as an argument  
- Returns a function as its result  

---

### Example: Function as an Argument
```js
function greet(fn) {
  fn();
}

function sayHello() {
  console.log("Hello");
}

greet(sayHello); // Higher-order function
