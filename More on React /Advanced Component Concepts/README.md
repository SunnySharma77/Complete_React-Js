# Advanced Component Concepts in React

## 1. Understanding Higher-Order Components (HOC) in React
A **Higher-Order Component (HOC)** is a function that takes a component and returns a new component with additional functionality.

### Example: Creating an HOC for Authorization
```jsx
function withAuth(Component) {
    return function AuthenticatedComponent(props) {
        const isAuthenticated = true; // Example authentication logic
        return isAuthenticated ? <Component {...props} /> : <h1>Please log in</h1>;
    };
}

function Dashboard() {
    return <h1>Welcome to your dashboard!</h1>;
}

const ProtectedDashboard = withAuth(Dashboard);
```

### Usage in `App.js`
```jsx
function App() {
    return <ProtectedDashboard />;
}
```

---

## 2. Reusing Components Efficiently
Reusable components help maintain clean and scalable code.

### Example: Generic Button Component
```jsx
function Button({ text, onClick, style }) {
    return (
        <button onClick={onClick} style={style}>
            {text}
        </button>
    );
}
```

### Usage with Different Props
```jsx
<Button text="Click Me" onClick={() => alert("Clicked!")} style={{ background: "blue", color: "white" }} />
<Button text="Submit" onClick={() => console.log("Submitted")} style={{ background: "green", color: "white" }} />
```

---

## 3. Lists and Keys in React for Dynamic Rendering
When rendering lists in React, each item needs a **unique key** for efficient updates.

### Example: Rendering a List
```jsx
function UserList({ users }) {
    return (
        <ul>
            {users.map((user) => (
                <li key={user.id}>{user.name}</li>
            ))}
        </ul>
    );
}
```

### Usage in `App.js`
```jsx
const users = [
    { id: 1, name: "Alice" },
    { id: 2, name: "Bob" },
    { id: 3, name: "Charlie" }
];

<UserList users={users} />
```

---

## Conclusion
- **HOCs help reuse logic across multiple components.**
- **Reusable components improve maintainability and scalability.**
- **Keys in lists improve rendering efficiency and avoid unnecessary re-renders.**

