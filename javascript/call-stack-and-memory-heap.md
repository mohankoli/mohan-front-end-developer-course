# Call Stack and Memory Heap

The JavaScript engine does a lot of work for us, but **two of the biggest jobs** are:
- **Reading the code**
- **Executing the code**

To do this efficiently, JavaScript uses:
- The **Memory Heap** – to store and write data
- The **Call Stack** – to keep track of what’s executing, line by line

---

## 🧠 Memory Heap

The **Memory Heap** is:
- A place to store and write information
- Used to **allocate, use, and remove memory** as needed
- **Unordered**, like a storage room full of random boxes

### Example: Memory Allocation

```javascript
// Tell the memory heap to allocate memory for a number
const number = 11;

// Allocate memory for a string
const string = "some text";

// Allocate memory for an object and its values
const person = {
  first: "Brittney",
  last: "Postma"
};
