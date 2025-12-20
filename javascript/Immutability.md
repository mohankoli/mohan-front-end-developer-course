# 9. Immutability in JS 

## Definition
> Immutability means **data cannot be changed** once created.  
> Instead of modifying the original object/array, create a **new copy**.

---

## Why It Matters
- ✅ **Predictability:** Prevent accidental changes  
- ✅ **React Rendering:** Detects changes via new references  
- ✅ **Debugging / History:** Supports undo/redo features

---

## Example

### Mutable (bad)
```js
let user = { name: "Mohan" };
user.name = "Koli"; // mutates original object

### best practice

const user = { name: "Mohan" };
const updatedUser = { ...user, name: "Koli" }; // new object

