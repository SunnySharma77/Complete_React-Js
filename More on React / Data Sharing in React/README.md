# Data Sharing in React

## 1. Understanding Props Drilling and Its Challenges
**Props Drilling** occurs when data is passed through multiple intermediary components before reaching the intended child component. This can lead to unnecessary complexity and tightly coupled components.

### Example: Props Drilling Issue
```jsx
function App() {
    const user = "Alice";
    return <Parent user={user} />;
}

function Parent({ user }) {
    return <Child user={user} />;
}

function Child({ user }) {
    return <h1>Hello, {user}!</h1>;
}
```
**Problem:** The `user` prop is passed through `Parent` unnecessarily.

---

## 2. Techniques to Pass Data Effectively
To avoid props drilling, consider these approaches:

### **1. Context API (Best for Global State Management)**
React's Context API allows data to be accessed directly by deeply nested components without manually passing props.

#### Example:
```jsx
import { createContext, useContext } from "react";

const UserContext = createContext();

function App() {
    return (
        <UserContext.Provider value="Alice">
            <Child />
        </UserContext.Provider>
    );
}

function Child() {
    const user = useContext(UserContext);
    return <h1>Hello, {user}!</h1>;
}
```
**Advantage:** No need to pass props manually.

---

### **2. Lifting State Up (Best for Sibling Communication)**
Instead of passing data through multiple levels, move the state to the nearest common parent.

#### Example:
```jsx
function App() {
    const [user, setUser] = useState("Alice");
    return <Parent user={user} setUser={setUser} />;
}

function Parent({ user, setUser }) {
    return <Child user={user} setUser={setUser} />;
}

function Child({ user, setUser }) {
    return (
        <div>
            <h1>Hello, {user}!</h1>
            <button onClick={() => setUser("Bob")}>Change User</button>
        </div>
    );
}
```
**Advantage:** Efficient for passing state between siblings.

---

### **3. Using Custom Hooks (Best for Encapsulating Logic)**
Encapsulating shared logic in a custom hook simplifies data management.

#### Example:
```jsx
function useUser() {
    const [user, setUser] = useState("Alice");
    return { user, setUser };
}

function App() {
    const { user, setUser } = useUser();
    return <Child user={user} setUser={setUser} />;
}
```
**Advantage:** Keeps components clean and reusable.

---

## Conclusion
- **Props drilling** can lead to complexity; avoid it when possible.
- **Context API** is best for global state sharing.
- **Lifting state up** helps when siblings need to share data.
- **Custom hooks** allow reusability and cleaner code.
