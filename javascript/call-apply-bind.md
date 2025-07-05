# JavaScript: `call`, `apply`, and `bind` – Short Notes with Real-World Use Cases

These methods help control the `this` context of a function.

---

## 🔹 `call()`

- Invokes the function immediately.
- Pass arguments one by one.
- ✅ Useful when borrowing methods from other objects.

```js
function greet(city) {
  console.log(`Hello, I am ${this.name} from ${city}`);
}
const person = { name: "Mohan" };

greet.call(person, "Pune"); 
// Output: Hello, I am Mohan from Pune
