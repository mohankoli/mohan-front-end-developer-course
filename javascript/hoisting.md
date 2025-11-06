# Hoisting in JavaScript

**Hoisting** is a behavior in **JavaScript** where **variable and function declarations** are moved (or “hoisted”) to the top of their scope (either the global scope or the current function scope) **before code execution**.

This means that **you can use functions and variables before they are declared in the code**, though the behavior differs depending on how they are declared.

---

## 💡 How Hoisting Works

When JavaScript code is compiled, the engine first scans through the code and allocates memory for all **declarations** (not initializations).

So during execution:
- **Declarations** are known to the interpreter.
- **Initializations** happen when the execution reaches that line.

---

## 🔹 Function Hoisting

Function **declarations** are fully hoisted — both their name and their body.

```js
sayHello(); // ✅ Works, even though defined later

function sayHello() {
  console.log("Hello!");
}

# Variable Hoisting in JavaScript

Variables declared with `var`, `let`, and `const` are **hoisted differently**.

| Declaration Type | Hoisted? | Initialized to `undefined`? | Accessible before declaration? |
|------------------|-----------|-----------------------------|--------------------------------|
| `var`            | ✅ Yes    | ✅ Yes                      | ⚠️ Yes, but `undefined`        |
| `let`            | ✅ Yes    | ❌ No                       | ❌ No (Temporal Dead Zone)     |
| `const`          | ✅ Yes    | ❌ No                       | ❌ No (Temporal Dead Zone)     |

---

## Example with `var`

```js
console.log(x); // undefined
var x = 10;

console.log(y); // ❌ ReferenceError
let y = 10;

