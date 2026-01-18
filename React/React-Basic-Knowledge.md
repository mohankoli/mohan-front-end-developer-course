# React Basic Knowledge

## --- What is this section about?---
This section covers foundational React concepts like JSX, Virtual DOM, components, props, state, rendering logic, child-parent communication, and styling. These concepts form the base of understanding how React builds UI and manages data flow.

## 7. What is Virtual DOM?
Virtual DOM (VDOM) is an in-memory lightweight representation of the actual browser DOM. React updates the Virtual DOM first, computes a diff, and then applies only the necessary changes to the real DOM using a reconciliation algorithm. 

Flow: State Change → Virtual DOM Render → Diff → Patch Real DOM

Benefits:
- minimizes DOM operations
- enhances performance
- enables declarative UI

## 8. What is JSX?
JSX (JavaScript XML) allows writing UI in JavaScript using HTML-like syntax.

Example:
```jsx
const element = <h1>Hello React</h1>;
```

JSX compiles to:
```js
React.createElement('h1', null, 'Hello React');
```

## 9. Why className and not class?
`class` is a reserved keyword in JavaScript. React uses `className` to avoid conflicts.

## 10. What are functional components and props?
Functional components are simple JS functions returning JSX and receive inputs via props.

Example:
```jsx
function Button({ label }) {
  return <button>{label}</button>;
}
```

## 11. What are class components, props and state?
Before hooks, class components held state and lifecycle:

```jsx
class Counter extends React.Component {
  state = { count: 0 };
  render() { return <h1>{this.state.count}</h1>; }
}
```

Props = external & read-only, State = internal & mutable.

## 12. Dumb vs Smart Components
- Dumb (Presentational): UI only, no state
- Smart (Container): manages data, state, async ops

## 13. What is a key in index map?
Keys help React identify items in lists for reconciliation.

```jsx
items.map(item => <li key={item.id}>{item.name}</li>)
```

Avoid index as key unless list is static.

## 14. What is React.Fragment?
Lets you group children without extra DOM wrappers:

```jsx
<>
  <h1>Title</h1>
  <p>Subtitle</p>
</>
```

## 15. What is conditional rendering?
Rendering different UI based on conditions:

```jsx
condition && <A/>
condition ? <A/> : <B/>
```

## 16. How to apply styles in React?
Methods:
- Inline styles
- CSS files
- CSS Modules
- Styled-components
- TailwindCSS
- UI libraries

## 17. Parent-child communication?
React uses unidirectional data flow.

Parent → Child via props  
Child → Parent via callback props

```jsx
function Parent() {
  const onChild = v => console.log(v);
  return <Child onEvent={onChild}/>
}
```
