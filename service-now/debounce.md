# 📌 Debounce in JavaScript

## 🔹 Simple Definition
Debounce is used to **prevent frequent calls** to a function.  
It delays the execution until the user **stops interacting**, such as during:
- Button clicks
- Scroll events
- Mouseover/mousemove
- Typing/input changes

---

## 🔹 Technical Definition
**Debounce** is a technique used to control how often a function is executed.  
It ensures that the function runs **only after a certain delay** has passed since the last call.  
This helps improve performance by avoiding unnecessary or rapid-fire executions.

---

## 🔹 Use Cases
- Button click handling
- API calls on input/typing
- Window resize or scroll events
- Search/autocomplete functionality

---

## ✅ Debounce Code Example

```html
<!-- HTML -->
<button id="btn">Click Me</button>

<style>
  button {
    height: 60px;
    width: 70px;
  }
</style>

<script>
  // Debounce Function
  function debounce(fn, delay) {
  let id;
  return () => {
    clearTimeout(id);
    id = setTimeout(fn,delay);
  }
}


let button = document.getElementById('btn');
button.onclick = debounce(()=>console.log('ordered'), 2000);
</script>
