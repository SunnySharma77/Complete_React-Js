# Introduction to React Hooks

## 1. What are Hooks, and Why Do We Use Them?
React **Hooks** allow functional components to use state and other React features without writing class components. Introduced in React 16.8, Hooks simplify component logic and improve code reusability.

### **Why Use Hooks?**
- **Avoid Class Components** – Hooks enable state management in function components.
- **Cleaner Code** – Reduces boilerplate compared to lifecycle methods in class components.
- **Reusable Logic** – Custom Hooks allow logic to be shared across components.
- **Better Performance** – Encourages optimized rendering patterns.

---

## 2. Understanding `useState`, `useEffect`, and Their Applications

### **2.1 `useState` Hook (Managing State in Functional Components)**
`useState` allows components to hold and update local state.

#### **Example: Counter with `useState`**
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

### **2.2 `useEffect` Hook (Handling Side Effects)**
`useEffect` manages side effects like API calls, subscriptions, and manual DOM manipulations.

#### **Example: Fetching Data with `useEffect`**
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
- The effect runs **once** when the component mounts.
- `setData` updates the state with fetched data.

#### **`useEffect` Dependency Array Variants**
| Dependency Array | When Effect Runs |
|-----------------|----------------|
| `useEffect(fn, [])` | Runs only on mount |
| `useEffect(fn, [state])` | Runs when `state` changes |
| `useEffect(fn)` | Runs after every render |
| `useEffect(() => fn(), [])` | Runs on mount, `fn()` executes on unmount |

---

## 3. Rules of Hooks and Best Practices
### **Rules of Hooks**
1. **Only Call Hooks at the Top Level** – Don't use Hooks inside loops, conditions, or nested functions.
2. **Only Call Hooks from React Functions** – Use Hooks only inside function components or custom Hooks.
3. **Follow the Order of Hooks** – React must call Hooks in the same order every time.

### **Best Practices**
- **Use `useState` sparingly** – Avoid excessive re-renders by grouping related state.
- **Use `useEffect` wisely** – Depend only on necessary variables to prevent unnecessary executions.
- **Optimize performance** – Use `useMemo` and `useCallback` for expensive calculations and event handlers.
- **Extract logic into custom Hooks** – Encapsulate reusable logic in custom Hooks.

---

## 4. Creating and Using Custom Hooks
Custom Hooks allow the reuse of stateful logic across multiple components.

### **Example: Creating a `useFetch` Hook**
```jsx
import { useState, useEffect } from "react";

function useFetch(url) {
    const [data, setData] = useState(null);
    const [loading, setLoading] = useState(true);

    useEffect(() => {
        fetch(url)
            .then(response => response.json())
            .then(json => {
                setData(json);
                setLoading(false);
            });
    }, [url]);

    return { data, loading };
}
```

### **Using `useFetch` in a Component**
```jsx
function Posts() {
    const { data, loading } = useFetch("https://jsonplaceholder.typicode.com/posts");

    if (loading) return <p>Loading...</p>;

    return (
        <ul>
            {data.slice(0, 5).map(post => (
                <li key={post.id}>{post.title}</li>
            ))}
        </ul>
    );
}
```

---

## 5. Summary
| Hook | Purpose |
|------|---------|
| `useState` | Manages component state |
| `useEffect` | Handles side effects like API calls |
| `useMemo` | Memoizes expensive calculations |
| `useCallback` | Memoizes functions to prevent unnecessary re-renders |
| `useContext` | Shares state without props drilling |
| `useRef` | Persists values without causing re-renders |

By understanding Hooks, developers can write **cleaner, reusable, and more efficient** React code!

