# JavaScript Closures

In simple terms, **closure** is a feature in JavaScript where an inner function has access to the variables and parameters of its outer function, even after the outer function has returned.

## Key Points
- A closure remembers the scope in which it was created.
- Inner functions can access outer function variables.
- Used to create private variables or function factories.

## Example

```javascript
function example() {
  let blog = "learnersbucket";
  
  function displayBlog() {
    console.log(blog); // Inner function accessing outer variable
  }

  displayBlog();
}

example();
// Output: "learnersbucket"
