# EventEmitter – Simple Publisher/Subscriber in JavaScript

This is a very easy implementation of an **EventEmitter**, often asked in interviews.  
It supports:

- `on(event, fn)` → subscribe  
- `emit(event, args)` → publish  
- `off(event)` → clear all listeners  

---

## Code

```js
function EventEmitter() {
    let events = {};
    return {
        on(event, fn) {
            events[event] = events[event] ? events[event] : [];
            events[event].push(fn);
        },
        off(event) {
            events[event] = [];
        },
        emit(event, ...args) {
             events[event] = events[event] ? events[event] : [];
             events[event].forEach(fn => fn(...args));
        }
    }
}
```

---

## Usage Example

```js
const emitter = EventEmitter();

function sayHello(name) {
  console.log("Hello " + name);
}

emitter.on("hi", sayHello);

emitter.emit("hi", "Mohan");  // Output: Hello Mohan

emitter.off("hi");            // remove all "hi" listeners

emitter.emit("hi", "Koli");   // No output (listeners removed)
```

---

## Concepts

### ✔ Publisher/Subscriber Pattern
- **Publisher** → sends events  
- **Subscriber** → listens for events  
- EventEmitter manages communication between them.

### ✔ Why interviewers ask this?
It tests:
- Closures  
- Objects  
- Arrays  
- Basic data structures  
- Understanding of observers/events  
