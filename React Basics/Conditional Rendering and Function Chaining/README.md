# Conditional Rendering and Function Chaining in React

## 1. Conditional Rendering in React
Conditional rendering allows components to display different content based on certain conditions.

### Using `if` Statements
```jsx
function Greeting({ isLoggedIn }) {
    if (isLoggedIn) {
        return <h1>Welcome back!</h1>;
    } else {
        return <h1>Please log in.</h1>;
    }
}
```

### Using Ternary Operator
```jsx
function Greeting({ isLoggedIn }) {
    return <h1>{isLoggedIn ? "Welcome back!" : "Please log in."}</h1>;
}
```

### Using Logical `&&` Operator (Short-circuiting)
```jsx
function Notification({ hasMessages }) {
    return (
        <div>
            <h1>Dashboard</h1>
            {hasMessages && <p>You have new messages!</p>}
        </div>
    );
}
```

---

## 2. Rendering Array Data Using `.map()`
`.map()` helps render lists dynamically from arrays.

### Example: Rendering a List of Items
```jsx
function ItemList({ items }) {
    return (
        <ul>
            {items.map((item, index) => (
                <li key={index}>{item}</li>
            ))}
        </ul>
    );
}
```

### Usage
```jsx
const items = ["Apple", "Banana", "Cherry"];
<ItemList items={items} />
```

---

## 3. Eliminating Array Data Using `.filter()`
`.filter()` is used to remove elements based on conditions.

### Example: Filtering Items
```jsx
function FilteredList({ items, query }) {
    const filteredItems = items.filter(item => item.toLowerCase().includes(query.toLowerCase()));

    return (
        <ul>
            {filteredItems.map((item, index) => (
                <li key={index}>{item}</li>
            ))}
        </ul>
    );
}
```

### Usage
```jsx
const fruits = ["Apple", "Banana", "Cherry", "Grapes"];
<FilteredList items={fruits} query="ap" />
```

---

## Conclusion
- **Use `if`, ternary, and `&&` for conditional rendering.**
- **`.map()` is useful for rendering lists dynamically.**
- **`.filter()` helps exclude unwanted data efficiently.**

