# Advanced React Hooks

## 1. `useRef` – Accessing and Manipulating DOM Elements
`useRef` is a Hook that provides a way to reference and manipulate DOM elements or persist values across renders without triggering a re-render.

### **Example: Accessing an Input Field**
```jsx
import { useRef } from "react";

function FocusInput() {
    const inputRef = useRef(null);

    const handleFocus = () => {
        inputRef.current.focus();
    };

    return (
        <div>
            <input ref={inputRef} type="text" placeholder="Type here..." />
            <button onClick={handleFocus}>Focus Input</button>
        </div>
    );
}

export default FocusInput;
```
- `useRef(null)` creates a reference to an input element.
- `inputRef.current.focus()` allows direct manipulation of the DOM element.

---

## 2. `useCallback` – Optimizing Function References in React
`useCallback` memoizes a function, preventing unnecessary re-creation on re-renders, which is useful when passing callbacks to child components.

### **Example: Preventing Unnecessary Function Re-Creation**
```jsx
import { useState, useCallback } from "react";
import ChildComponent from "./ChildComponent";

function ParentComponent() {
    const [count, setCount] = useState(0);

    const increment = useCallback(() => {
        setCount(prev => prev + 1);
    }, []); // Function remains the same across re-renders

    return (
        <div>
            <h1>Count: {count}</h1>
            <ChildComponent increment={increment} />
        </div>
    );
}

export default ParentComponent;
```
- `useCallback(increment, [])` ensures `increment` does not get recreated on each render.
- Useful in performance optimization when passing functions as props to child components.

---

## 3. `useMemo` – Enhancing Performance with Memoization
`useMemo` caches the result of an expensive computation and only recalculates when dependencies change.

### **Example: Memoizing Expensive Calculations**
```jsx
import { useState, useMemo } from "react";

function ExpensiveComponent() {
    const [count, setCount] = useState(0);
    const [input, setInput] = useState("");

    const expensiveCalculation = (num) => {
        console.log("Calculating...");
        return num * 2;
    };

    const computedValue = useMemo(() => expensiveCalculation(count), [count]);

    return (
        <div>
            <h1>Computed Value: {computedValue}</h1>
            <button onClick={() => setCount(count + 1)}>Increase Count</button>
            <input value={input} onChange={(e) => setInput(e.target.value)} placeholder="Type something..." />
        </div>
    );
}

export default ExpensiveComponent;
```
- `useMemo` ensures `expensiveCalculation(count)` runs only when `count` changes.
- Improves performance by avoiding redundant recalculations on re-renders.

---

## Summary
| Hook | Purpose |
|------|---------|
| `useRef` | Directly references and manipulates DOM elements |
| `useCallback` | Optimizes function references, preventing unnecessary re-creation |
| `useMemo` | Enhances performance by memoizing expensive calculations |

By mastering these advanced Hooks, you can build more efficient, optimized, and scalable React applications.
