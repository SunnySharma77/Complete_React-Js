# Styling Components in React

## 1. Importing CSS Files and Stylesheets into React
The simplest way to style a React component is by using standard CSS files.

### Example: Using an External CSS File
#### `styles.css`
```css
.container {
    background-color: lightblue;
    padding: 20px;
    text-align: center;
}
```

#### `App.js`
```jsx
import "./styles.css";

function App() {
    return <div className="container">Hello, Styled World!</div>;
}

export default App;
```

---

## 2. Adding and Using CSS Modules
CSS Modules provide **scoped styles** to prevent conflicts.

### Example: Using CSS Modules
#### `Button.module.css`
```css
.button {
    background-color: blue;
    color: white;
    padding: 10px;
    border: none;
    cursor: pointer;
}
```

#### `Button.js`
```jsx
import styles from "./Button.module.css";

function Button({ text }) {
    return <button className={styles.button}>{text}</button>;
}

export default Button;
```

#### Usage in `App.js`
```jsx
import Button from "./Button";

function App() {
    return <Button text="Click Me" />;
}
```

---

## 3. Introduction to Styled Components and Dynamic Styling
Styled-components allow writing CSS-in-JS, making components more modular and dynamic.

### Installing Styled Components
```sh
npm install styled-components
```

### Example: Styled Components in React
#### `Button.js`
```jsx
import styled from "styled-components";

const StyledButton = styled.button`
    background-color: ${(props) => (props.primary ? "blue" : "gray")};
    color: white;
    padding: 10px;
    border: none;
    cursor: pointer;
    &:hover {
        background-color: ${(props) => (props.primary ? "darkblue" : "darkgray")};
    }
`;

function Button({ text, primary }) {
    return <StyledButton primary={primary}>{text}</StyledButton>;
}

export default Button;
```

#### Usage in `App.js`
```jsx
function App() {
    return (
        <div>
            <Button text="Primary Button" primary />
            <Button text="Secondary Button" />
        </div>
    );
}
```

---

## Conclusion
- **Use CSS files for global styles.**
- **Use CSS Modules for scoped styles to prevent conflicts.**
- **Use Styled Components for dynamic, component-specific styles.**
- Choose the approach based on project complexity and scalability.

