# Parameterized Function Components in React

## 1. Creating and Using Parameterized Function Components
Parameterized function components allow us to pass data dynamically through **props**, making components reusable and flexible.

### Example: Basic Parameterized Component
```jsx
function Greeting({ name }) {
    return <h1>Hello, {name}!</h1>;
}
```

### Usage in Another Component
```jsx
function App() {
    return (
        <div>
            <Greeting name="Alice" />
            <Greeting name="Bob" />
        </div>
    );
}
```
---

## 2. Understanding React Props for Passing Data Between Components
**Props** (short for "properties") are read-only arguments passed from parent to child components.

### Example: Passing Multiple Props
```jsx
function UserProfile({ name, age, isMember }) {
    return (
        <div>
            <h2>Name: {name}</h2>
            <p>Age: {age}</p>
            <p>Membership: {isMember ? "Active" : "Inactive"}</p>
        </div>
    );
}
```

### Usage in Parent Component
```jsx
function App() {
    return (
        <div>
            <UserProfile name="Alice" age={25} isMember={true} />
            <UserProfile name="Bob" age={30} isMember={false} />
        </div>
    );
}
```

### Default Props
To avoid errors when a prop isn't provided, use default values:
```jsx
function Welcome({ message = "Welcome to React!" }) {
    return <h2>{message}</h2>;
}
```

### Prop Types Validation (Using `prop-types`)
To enforce expected prop types:
```sh
npm install prop-types
```
```jsx
import PropTypes from "prop-types";

function UserProfile({ name, age }) {
    return (
        <div>
            <h2>{name}</h2>
            <p>Age: {age}</p>
        </div>
    );
}

UserProfile.propTypes = {
    name: PropTypes.string.isRequired,
    age: PropTypes.number.isRequired,
};
```

---

## Conclusion
- **Parameterized components make UI reusable and dynamic.**
- **Props allow data transfer between parent and child components.**
- **Default props prevent missing value errors.**
- **Prop types help validate props for better debugging.**

