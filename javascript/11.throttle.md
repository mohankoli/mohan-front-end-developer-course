# Throttle in JavaScript

## 🔍 Definition

**Throttle** is a technique used to **limit the number of times a function is called** over time. It ensures that a function is called at most once every specified delay interval, no matter how many times the event is triggered.

It is especially useful for performance optimization in high-frequency events like:
- `scroll`
- `resize`
- `mousemove`
- `click`

---

## ✅ Example: Throttle a Button Click

### 📄 HTML

```html
<button id="myid">Throttle me</button>

const throttle = (fn, delay) => {
  let last = 0;
  return function(...args) {
    const now = new Date().getTime();
    if (now - last < delay) {
      return;
    }
    last = now;
    fn(...args);
  };
};

document.getElementById('myid').addEventListener('click', throttle(() => {
  console.log('you clicked on me');
}, 5000));
