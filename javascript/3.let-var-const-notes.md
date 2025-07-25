# JavaScript: `var`, `let`, and `const` – Short Notes

- `var` is **function-scoped**. It is hoisted and initialized as `undefined`.
- `let` and `const` are **block-scoped**. They are hoisted but **not initialized** (Temporal Dead Zone).
- `var` allows both **reassignment** and **redeclaration**.
- `let` allows **reassignment**, but **not redeclaration** in the same scope.
- `const` does **not** allow **reassignment** or **redeclaration**.
- Use `const` when the variable value should not change.
- Use `let` when the value needs to change.
- Avoid `var` in modern JavaScript code.

## 🔍 Example

```js
var x = 1;
let y = 2;
const z = 3;

x = 10;   // ✅
y = 20;   // ✅
z = 30;   // ❌ Error: Assignment to constant variable
