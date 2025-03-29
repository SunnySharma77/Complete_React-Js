# React Components and JSX

## What Are Components?
Components are the building blocks of a React application. They allow developers to create reusable UI elements that can manage their own state and logic.

## Types of Components

### 1. Class Components
Class components are ES6 classes that extend `React.Component` and use the `render()` method to return JSX.

Example:
```jsx
import React, { Component } from 'react';

class Greeting extends Component {
    render() {
        return <h1>Hello, {this.props.name}!</h1>;
    }
}

export default Greeting;
```

### 2. Function Components
Function components are simpler and use hooks (like `useState`) for state management.

Example:
```jsx
import React from 'react';

function Greeting({ name }) {
    return <h1>Hello, {name}!</h1>;
}

export default Greeting;
```

## Understanding JSX (JavaScript XML)
JSX is a syntax extension for JavaScript that allows writing HTML-like structures inside JavaScript.

### Why is JSX Important?
- Makes UI code more readable and maintainable.
- Allows embedding JavaScript expressions inside HTML-like syntax.
- React components use JSX to define their structure.

Example:
```jsx
const element = <h1>Hello, World!</h1>;
```

## JSX Best Practices

### 1. Using Fragments (`<>...</>`)
React requires a single parent element, so we use fragments to avoid unnecessary `<div>` wrappers.

Example:
```jsx
function App() {
    return (
        <>
            <h1>Welcome</h1>
            <p>This is a React App.</p>
        </>
    );
}
```

### 2. Component Naming
- Use **PascalCase** for component names.
- Example: `MyComponent` instead of `mycomponent` or `my_component`.

### 3. Keeping Components Small and Focused
- Each component should have a single responsibility.
- Break down large components into smaller reusable ones.

## Conclusion
React's component-based approach and JSX make UI development efficient and scalable. Mastering these concepts helps in building maintainable and performant applications.

