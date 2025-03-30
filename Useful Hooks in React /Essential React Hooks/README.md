# Essential React Hooks

## 1. `useState` – Managing Component State
`useState` is a Hook that allows functional components to manage state.

### **Example: Counter with `useState`**
```jsx
import { useState } from "react";

function Counter() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <h1>Count: {count}</h1>
            <button onClick={() => setCount(count + 1)}>Increment</button>
        </div>
    );
}
```
- `useState(0)` initializes `count` with `0`.
- `setCount(count + 1)` updates state and triggers re-rendering.

---

## 2. `useEffect` – Handling Side Effects and Lifecycle Behavior
`useEffect` is used to perform side effects in function components (e.g., fetching data, subscriptions, manual DOM manipulations).

### **Example: Fetching Data with `useEffect`**
```jsx
import { useState, useEffect } from "react";

function DataFetcher() {
    const [data, setData] = useState([]);

    useEffect(() => {
        fetch("https://jsonplaceholder.typicode.com/posts")
            .then(response => response.json())
            .then(json => setData(json));
    }, []); // Empty dependency array means it runs once on mount

    return (
        <ul>
            {data.slice(0, 5).map(item => (
                <li key={item.id}>{item.title}</li>
            ))}
        </ul>
    );
}
```
- Runs **once** when the component mounts.
- Fetches data and updates state using `setData`.

#### **`useEffect` Dependency Array Variants**
| Dependency Array | When Effect Runs |
|-----------------|----------------|
| `useEffect(fn, [])` | Runs only on mount |
| `useEffect(fn, [state])` | Runs when `state` changes |
| `useEffect(fn)` | Runs after every render |
| `useEffect(() => fn(), [])` | Runs on mount, `fn()` executes on unmount |

---

## 3. `useContext` – Simplifying State Management with Context API
`useContext` allows functional components to consume context without prop drilling.

### **Example: Using `useContext` to Manage Theme**
```jsx
import { createContext, useState, useContext } from "react";

const ThemeContext = createContext();

function App() {
    const [theme, setTheme] = useState("light");

    return (
        <ThemeContext.Provider value={{ theme, setTheme }}>
            <ChildComponent />
        </ThemeContext.Provider>
    );
}

function ChildComponent() {
    const { theme, setTheme } = useContext(ThemeContext);

    return (
        <div>
            <p>Current Theme: {theme}</p>
            <button onClick={() => setTheme(theme === "light" ? "dark" : "light")}>Toggle Theme</button>
        </div>
    );
}

export default App;
```
- `ThemeContext.Provider` supplies `theme` and `setTheme`.
- `useContext(ThemeContext)` extracts values in `ChildComponent`.

---

## Summary
| Hook | Purpose |
|------|---------|
| `useState` | Manages component state |
| `useEffect` | Handles side effects and lifecycle behavior |
| `useContext` | Simplifies state management and avoids prop drilling |

By mastering these essential Hooks, you can efficiently manage state and side effects in React applications.

