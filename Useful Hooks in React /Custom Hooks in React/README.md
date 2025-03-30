# Custom Hooks in React

## 1. What Are Custom Hooks, and When to Use Them?
Custom Hooks are reusable JavaScript functions in React that encapsulate component logic and stateful behavior. They allow sharing logic between components without repeating code.

### **When to Use Custom Hooks?**
- When multiple components share the same logic.
- When you need to abstract API calls, event listeners, or state management.
- When you want to simplify complex logic inside components.

---

## 2. Creating and Structuring Custom Hooks for Reusability
A Custom Hook is a JavaScript function that starts with `use` and can call other Hooks inside it.

### **Example: Creating a `useFetch` Custom Hook**
```jsx
import { useState, useEffect } from "react";

function useFetch(url) {
    const [data, setData] = useState(null);
    const [loading, setLoading] = useState(true);
    const [error, setError] = useState(null);

    useEffect(() => {
        setLoading(true);
        fetch(url)
            .then(response => response.json())
            .then(data => {
                setData(data);
                setLoading(false);
            })
            .catch(err => {
                setError(err);
                setLoading(false);
            });
    }, [url]);

    return { data, loading, error };
}

export default useFetch;
```

### **Using `useFetch` in a Component**
```jsx
import React from "react";
import useFetch from "./useFetch";

function PostList() {
    const { data, loading, error } = useFetch("https://jsonplaceholder.typicode.com/posts");

    if (loading) return <p>Loading...</p>;
    if (error) return <p>Error: {error.message}</p>;

    return (
        <ul>
            {data.slice(0, 5).map(post => (
                <li key={post.id}>{post.title}</li>
            ))}
        </ul>
    );
}

export default PostList;
```
- `useFetch` simplifies fetching logic by handling data fetching, errors, and loading states.
- Any component using `useFetch` gets clean and readable code.

---

## 3. Best Practices for Writing Efficient Hooks
- **Prefix Hook Names with `use`** – Ensures they follow React’s Hook naming convention (`useFetch`, `useAuth`).
- **Keep Hooks Pure** – Avoid modifying state or calling functions inside the Hook that don’t belong there.
- **Use Dependencies Carefully** – Optimize `useEffect` dependencies to prevent unnecessary re-renders.
- **Ensure Reusability** – Make Hooks flexible by using parameters and returning only relevant data.
- **Combine Hooks If Needed** – If multiple Hooks share logic, consider composing them into a single Hook.

### **Example: Combining Hooks (`useToggle`)**
```jsx
import { useState } from "react";

function useToggle(initialValue = false) {
    const [state, setState] = useState(initialValue);

    const toggle = () => setState(prevState => !prevState);

    return [state, toggle];
}

export default useToggle;
```

### **Using `useToggle` in a Component**
```jsx
import useToggle from "./useToggle";

function ThemeSwitcher() {
    const [isDark, toggleTheme] = useToggle(false);

    return (
        <div>
            <p>Current Theme: {isDark ? "Dark Mode" : "Light Mode"}</p>
            <button onClick={toggleTheme}>Toggle Theme</button>
        </div>
    );
}

export default ThemeSwitcher;
```
- `useToggle` provides a reusable way to toggle boolean values.
- Components using `useToggle` stay simple and maintainable.

---

## Summary
| Custom Hook | Purpose |
|------------|---------|
| `useFetch` | Handles API fetching, errors, and loading states |
| `useToggle` | Provides an easy way to toggle a boolean state |

By mastering Custom Hooks, you can create efficient, reusable, and scalable solutions in your React applications!

