# once(fn) — Run a Function Only Once (Using call())

```javascript
function once(fn) {
  let done = false;

  return function (...args) {
    if (!done) {
      done = true;
      return fn.call(this, ...args);
    }
  };
}

function hello(name) {
  console.log("Hello " + name);
}

const runOnce = once(hello);

runOnce("Mohan"); // prints "Hello Mohan"
runOnce("Koli");  // does nothing
runOnce("XYZ");   // does nothing
