# React Basic Knowledge

## --- What is this section about?---
This section covers foundational React concepts like JSX, Virtual DOM, components, props, state, rendering logic, child-parent communication, and styling. These concepts form the base of understanding how React builds UI and manages data flow.

## 1. What is Virtual DOM?
Virtual DOM (VDOM) is an in-memory lightweight representation of the actual browser DOM. React updates the Virtual DOM first, computes a diff, and then applies only the necessary changes to the real DOM using a reconciliation algorithm. 

Flow: State Change → Virtual DOM Render → Diff → Patch Real DOM

Benefits:
- minimizes DOM operations
- enhances performance
- enables declarative UI

## 2. What is JSX?
JSX means writing HTML inside JavaScript. JSX (JavaScript XML) allows writing UI in JavaScript using HTML-like syntax.

Example:
```jsx
const element = <h1>Hello React</h1>;
```

JSX compiles to:
```js
React.createElement('h1', null, 'Hello React');
```

## 3. Why className and not class?
`class` is a reserved keyword in JavaScript. React uses `className` to avoid conflicts.

## 4. What are functional components and props?
Functional components are simple JS functions returning JSX and receive inputs via props.

Example:
```jsx
function Button({ label }) {
  return <button>{label}</button>;
}
```

## 5. What are class components, props and state?
Before hooks, class components held state and lifecycle:

```jsx
class Counter extends React.Component {
  state = { count: 0 };
  render() { return <h1>{this.state.count}</h1>; }
}
```

Props = external & read-only, State = internal & mutable.

## 6. Dumb vs Smart Components
- Dumb (Presentational): UI only, no state
- Smart (Container): manages data, state, async ops

## 7. What is a key in index map?
- A **key** is a unique identifier for list items rendered using `.map()` in React, helping React track which item changed, got added, or removed.
- Keys improve rendering performance and reconciliation by preventing unnecessary re-renders.
- Preferred keys come from unique fields like `id` or `uuid`; using `index` is only recommended for static lists.
- Incorrect or unstable keys can cause UI bugs, such as incorrect item updates or preserved state in wrong elements.

```jsx
items.map(item => <li key={item.id}>{item.name}</li>)
```

Avoid index as key unless list is static.

## 8. What is React.Fragment?
- `React.Fragment` lets you group multiple elements without adding extra DOM nodes.
- It avoids unnecessary wrapper elements like `<div>` which can break styling or layouts.
- It is useful when returning multiple children from a component.
- It can be written as `<React.Fragment>` or the shorthand `<>...</>`.


```jsx
<>
  <h1>Title</h1>
  <p>Subtitle</p>
</>
```

## 9. What is conditional rendering?
- Conditional rendering means showing different UI based on certain conditions or state.
- It allows React components to render specific elements only when a condition is true.
- Commonly used for scenarios like loading states, authentication, feature toggles, and empty states.
- It is implemented using JS logic such as `&&`, ternary (`? :`), and `if` statements inside JSX.


```jsx
condition && <A/>
condition ? <A/> : <B/>
```

## 10. How to apply styles in React?

React supports multiple styling approaches:

- **Inline Styles** — Styles defined directly inside JSX using style objects. Good for dynamic styles but limited (no pseudo selectors).
- **CSS Files** — Traditional `.css` imported into components. Simple and widely used for global or scoped styles.
- **CSS Modules** — Locally scoped CSS feature (`.module.css`) avoiding class name collisions; better for scaling apps.
- **Styled-Components (CSS-in-JS)** — Styles written as components with support for props, theming, and dynamic styling.
- **TailwindCSS** — Utility-first CSS framework helping quickly build UI using predefined classes; good for consistency and speed.
- **UI Libraries** (e.g., MUI, AntD, Chakra) — Provide pre-styled components for faster development and consistent design systems.


## 11. Parent-child communication?

- React uses **unidirectional (one-way) data flow**, meaning data always flows from parent to child.
- **Parent → Child:** done using `props` to pass data or configuration down the tree.
- **Child → Parent:** done using callback functions passed from the parent, allowing the child to trigger updates or send values back.
- This pattern makes data flow predictable, easier to debug, and helps maintain component state ownership.


React uses unidirectional data flow.

Parent → Child via props  
Child → Parent via callback props

```jsx
function Parent() {
  const onChild = v => console.log(v);
  return <Child onEvent={onChild}/>
}
```
---

## 12. Difference between Functional and Class Components

### (Why hooks replaced classes?)

| Feature           | Class Component  | Functional Component |
| ----------------- | ---------------- | -------------------- |
| Syntax            | ES6 Classes      | JavaScript Functions |
| State             | `this.state`     | `useState`           |
| Lifecycle methods | Yes              | Via Hooks            |
| `this` keyword    | Required         | Not required         |
| Code size         | More boilerplate | Cleaner & shorter    |
| Reusability       | Limited          | High (custom hooks)  |
| Performance       | Slightly heavier | Lightweight          |
