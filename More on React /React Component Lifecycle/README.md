# React Component Lifecycle

## 1. What is the Component Lifecycle in React?
The **component lifecycle** in React refers to the sequence of events that occur from the creation of a component to its removal from the DOM. React components go through different phases: **Mounting, Updating, and Unmounting**.

---

## 2. Lifecycle Phases
### **Mounting (Component Creation & Insertion into the DOM)**
Occurs when a component is created and inserted into the DOM.
- **Commonly Used Lifecycle Method:** `componentDidMount()` (Class Components) / `useEffect()` (Function Components)

### **Updating (Component Re-rendering Due to State or Props Changes)**
Occurs when a component updates due to a state or prop change.
- **Commonly Used Lifecycle Method:** `componentDidUpdate()` / `useEffect()`

### **Unmounting (Component Removal from the DOM)**
Occurs when a component is removed from the DOM.
- **Commonly Used Lifecycle Method:** `componentWillUnmount()` / `useEffect()` (Cleanup Function)

---

## 3. Key Lifecycle Methods
### **Class Component Lifecycle Methods**
#### **1. `componentDidMount()` (Runs After Component is Mounted)**
```jsx
class Example extends React.Component {
    componentDidMount() {
        console.log("Component Mounted!");
    }
    render() {
        return <h1>Hello, World!</h1>;
    }
}
```
- **Used for:** API calls, event listeners, subscriptions.

#### **2. `componentDidUpdate(prevProps, prevState)` (Runs After Component Updates)**
```jsx
class Example extends React.Component {
    componentDidUpdate(prevProps, prevState) {
        console.log("Component Updated!");
    }
    render() {
        return <h1>Updated Component!</h1>;
    }
}
```
- **Used for:** Reacting to prop/state changes, API calls after updates.

#### **3. `componentWillUnmount()` (Runs Before Component Unmounts)**
```jsx
class Example extends React.Component {
    componentWillUnmount() {
        console.log("Component Unmounted!");
    }
    render() {
        return <h1>Goodbye, World!</h1>;
    }
}
```
- **Used for:** Cleaning up event listeners, cancelling API requests.

---

## 4. Lifecycle Methods in Functional Components (Using `useEffect`)
Functional components use the `useEffect` hook to handle lifecycle behaviors.

### **Mounting (`componentDidMount`)**
```jsx
import { useEffect } from "react";

function Example() {
    useEffect(() => {
        console.log("Component Mounted!");
    }, []); // Empty dependency array ensures it runs only once

    return <h1>Hello, World!</h1>;
}
```

### **Updating (`componentDidUpdate`)**
```jsx
import { useEffect, useState } from "react";

function Example() {
    const [count, setCount] = useState(0);

    useEffect(() => {
        console.log("Component Updated!");
    }, [count]); // Runs when `count` changes

    return <button onClick={() => setCount(count + 1)}>Click Me</button>;
}
```

### **Unmounting (`componentWillUnmount`)**
```jsx
import { useEffect } from "react";

function Example() {
    useEffect(() => {
        console.log("Component Mounted!");

        return () => {
            console.log("Component Unmounted!");
        };
    }, []);

    return <h1>Goodbye, World!</h1>;
}
```

---

## 5. Summary
| Phase       | Class Component Method    | Functional Component (`useEffect`) |
|------------|--------------------------|----------------------------------|
| Mounting   | `componentDidMount()`     | `useEffect(() => {}, [])`       |
| Updating   | `componentDidUpdate()`    | `useEffect(() => {}, [dependency])` |
| Unmounting | `componentWillUnmount()`  | `useEffect(() => { return () => {} }, [])` |

---

By understanding these lifecycle methods, developers can manage component behavior efficiently, optimize performance, and ensure proper resource management.

