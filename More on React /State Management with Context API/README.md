# State Management with Context API

## 1. Understanding `useContext` and Its Role in State Management

The **Context API** in React provides a way to share state and functions between components without passing props manually at every level (prop drilling). The `useContext` hook allows functional components to consume context easily.

### **Why Use Context API?**
- **Avoid Prop Drilling** – Eliminates the need to pass props through multiple nested components.
- **Global State Management** – Makes state available to any component in the application.
- **Simplifies Code** – Reduces complexity compared to lifting state up.

---

## 2. Applying Context API to Avoid Excessive Prop Drilling

### **2.1 Creating a Context**
To use the Context API, first, create a context using `createContext()`.

```jsx
import { createContext } from "react";

const ThemeContext = createContext();
```

---

### **2.2 Providing Context**
Wrap the application (or part of it) with the `Provider` component to supply values.

```jsx
import React, { useState } from "react";
import { ThemeContext } from "./ThemeContext";
import ChildComponent from "./ChildComponent";

function App() {
    const [theme, setTheme] = useState("light");

    return (
        <ThemeContext.Provider value={{ theme, setTheme }}>
            <ChildComponent />
        </ThemeContext.Provider>
    );
}

export default App;
```
- The `ThemeContext.Provider` supplies `theme` and `setTheme` to child components.
- Any component inside `ThemeContext.Provider` can access these values.

---

### **2.3 Consuming Context with `useContext`**
Child components can now consume the provided context using `useContext`.

```jsx
import React, { useContext } from "react";
import { ThemeContext } from "./ThemeContext";

function ChildComponent() {
    const { theme, setTheme } = useContext(ThemeContext);

    return (
        <div>
            <p>Current Theme: {theme}</p>
            <button onClick={() => setTheme(theme === "light" ? "dark" : "light")}>Toggle Theme</button>
        </div>
    );
}

export default ChildComponent;
```
- `useContext(ThemeContext)` extracts `theme` and `setTheme`.
- Allows the component to update and consume global state without passing props.

---

## 3. When to Use Context API vs. Other State Management Solutions
| State Management Method | When to Use |
|------------------------|-------------|
| **Context API** | Sharing state across multiple components without prop drilling. |
| **useState** | Managing local component state. |
| **Redux/Zustand/Recoil** | Complex state management with multiple sources of truth. |

By using Context API effectively, you can streamline state management and improve code maintainability in your React applications.

