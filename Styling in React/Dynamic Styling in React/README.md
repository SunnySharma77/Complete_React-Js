# Dynamic Styling in React

## 1. Styling Components Dynamically Based on Props and State
React allows dynamic styling based on **props** and **state**, making UI customization more flexible.

### Example: Styling Based on Props
You can pass props to dynamically set styles.
```jsx
function Button({ primary }) {
    return (
        <button className={primary ? "bg-blue-500 text-white" : "bg-gray-300 text-black"}>
            Click Me
        </button>
    );
}

export default Button;
```
**Usage:**
```jsx
<Button primary={true} />  // Blue button
<Button primary={false} /> // Gray button
```

### Example: Styling Based on State
```jsx
import { useState } from "react";

function ToggleButton() {
    const [active, setActive] = useState(false);

    return (
        <button
            className={active ? "bg-green-500 text-white" : "bg-red-500 text-white"}
            onClick={() => setActive(!active)}
        >
            {active ? "Active" : "Inactive"}
        </button>
    );
}

export default ToggleButton;
```

---

## 2. Conditional Styling Techniques for Better UI Control

### 2.1 Using Template Literals
```jsx
function Card({ isHighlighted }) {
    return (
        <div className={`p-4 border ${isHighlighted ? "border-blue-500" : "border-gray-300"}`}>
            Conditional Styling Example
        </div>
    );
}
```

### 2.2 Using Inline Styles with Dynamic Values
```jsx
function DynamicBox({ size }) {
    return (
        <div style={{ width: `${size}px`, height: `${size}px`, backgroundColor: "blue" }}>
            Dynamic Size Box
        </div>
    );
}
```

### 2.3 Using CSS Modules for Conditional Classes
```css
/* styles.module.css */
.active {
    background-color: green;
    color: white;
}
.inactive {
    background-color: red;
    color: white;
}
```
```jsx
import styles from "./styles.module.css";

function StatusButton({ isActive }) {
    return (
        <button className={isActive ? styles.active : styles.inactive}>
            {isActive ? "Active" : "Inactive"}
        </button>
    );
}
```

### 2.4 Using TailwindCSS for Conditional Styling
If using **TailwindCSS**, use class conditionals:
```jsx
function Alert({ type }) {
    return (
        <div className={`p-4 ${type === "success" ? "bg-green-500" : "bg-red-500"}`}>
            {type === "success" ? "Success!" : "Error!"}
        </div>
    );
}
```

---

## Conclusion
Dynamic styling enhances UI flexibility in React. You can achieve this by using **props, state, template literals, inline styles, CSS modules, or TailwindCSS**. Using these techniques efficiently ensures a maintainable and scalable codebase.

