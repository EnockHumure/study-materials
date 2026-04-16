# React Fundamentals - Complete Beginner's Guide

## Table of Contents
1. [What is React?](#what-is-react)
2. [JSX - JavaScript XML](#jsx)
3. [Components](#components)
4. [Props](#props)
5. [State](#state)
6. [Hooks](#hooks)
7. [Event Handling](#event-handling)
8. [Conditional Rendering](#conditional-rendering)
9. [Lists and Keys](#lists-and-keys)
10. [Forms](#forms)
11. [Best Practices](#best-practices)

---

## What is React?

React is a JavaScript library for building user interfaces. Instead of manually updating the HTML when data changes, React automatically updates the page for you.

### Why React?
- **Reusable Components**: Build small pieces and combine them
- **Automatic Updates**: When data changes, React updates the page automatically
- **Easier to Manage**: Organize your code into smaller, manageable pieces

### Installation

```bash
# Create a new React app
npx create-react-app my-app
cd my-app
npm start
```

---

## JSX - JavaScript XML

JSX lets you write HTML-like code inside JavaScript. It looks like HTML but it's actually JavaScript.

### Basic JSX

```javascript
// JSX looks like HTML
const greeting = <h1>Hello, World!</h1>;

// But it's actually JavaScript
const greeting = React.createElement('h1', null, 'Hello, World!');

// You can use JavaScript expressions inside {}
const name = "Alice";
const message = <h1>Hello, {name}!</h1>;

// You can use any JavaScript expression
const age = 25;
const info = <p>I am {age} years old</p>;
const doubled = <p>Double: {age * 2}</p>;
```

### JSX Rules

```javascript
// 1. Return a single root element
// ❌ Wrong - multiple elements
const wrong = (
  <h1>Title</h1>
  <p>Paragraph</p>
);

// ✅ Correct - wrapped in one element
const correct = (
  <div>
    <h1>Title</h1>
    <p>Paragraph</p>
  </div>
);

// 2. Close all tags
// ❌ Wrong
const image = <img src="photo.jpg">;

// ✅ Correct
const image = <img src="photo.jpg" />;

// 3. Use className instead of class
// ❌ Wrong
const element = <div class="container">Content</div>;

// ✅ Correct
const element = <div className="container">Content</div>;

// 4. Use camelCase for attributes
// ❌ Wrong
const input = <input onclick="handleClick" />;

// ✅ Correct
const input = <input onClick={handleClick} />;
```

---

## Components

Components are reusable pieces of your UI. Think of them as functions that return JSX.

### Functional Components

```javascript
// Simple component
function Welcome() {
  return <h1>Welcome to React!</h1>;
}

// Component with parameters (props)
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

// Using the component
export default function App() {
  return (
    <div>
      <Welcome />
      <Greeting name="Alice" />
    </div>
  );
}
```

### Component Naming

```javascript
// ✅ Correct - starts with capital letter
function MyButton() {
  return <button>Click me</button>;
}

// ❌ Wrong - starts with lowercase
function myButton() {
  return <button>Click me</button>;
}
```

### Component File Structure

```
src/
├── components/
│   ├── Header.js
│   ├── Footer.js
│   └── Card.js
├── App.js
└── index.js
```

```javascript
// Header.js
function Header() {
  return <header>My Website</header>;
}

export default Header;
```

```javascript
// App.js
import Header from './components/Header';
import Footer from './components/Footer';

function App() {
  return (
    <div>
      <Header />
      <main>Content here</main>
      <Footer />
    </div>
  );
}

export default App;
```

---

## Props

Props are how you pass data from a parent component to a child component. Think of them like function parameters.

### Passing Props

```javascript
// Parent component
function App() {
  return (
    <div>
      <Card title="My Card" description="This is a card" />
      <Card title="Another Card" description="Another description" />
    </div>
  );
}

// Child component receives props
function Card(props) {
  return (
    <div className="card">
      <h2>{props.title}</h2>
      <p>{props.description}</p>
    </div>
  );
}
```

### Destructuring Props

```javascript
// Instead of props.title and props.description
function Card(props) {
  return (
    <div>
      <h2>{props.title}</h2>
      <p>{props.description}</p>
    </div>
  );
}

// You can destructure them
function Card({ title, description }) {
  return (
    <div>
      <h2>{title}</h2>
      <p>{description}</p>
    </div>
  );
}
```

### Default Props

```javascript
function Button({ text = "Click me", color = "blue" }) {
  return <button style={{ backgroundColor: color }}>{text}</button>;
}

// Usage
<Button /> // Uses defaults
<Button text="Submit" /> // Uses custom text, default color
<Button text="Submit" color="green" /> // Uses both custom values
```

### Props are Read-Only

```javascript
// ❌ Wrong - don't modify props
function Card({ title }) {
  title = "New Title"; // Don't do this!
  return <h2>{title}</h2>;
}

// ✅ Correct - use state if you need to change it
import { useState } from 'react';

function Card({ title }) {
  const [cardTitle, setCardTitle] = useState(title);
  
  const handleChange = () => {
    setCardTitle("New Title");
  };
  
  return (
    <div>
      <h2>{cardTitle}</h2>
      <button onClick={handleChange}>Change Title</button>
    </div>
  );
}
```

---

## State

State is data that can change over time. When state changes, React automatically updates the component.

### Using useState Hook

```javascript
import { useState } from 'react';

function Counter() {
  // Declare state variable
  // count = current value
  // setCount = function to update it
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>
        Increment
      </button>
    </div>
  );
}
```

### Multiple State Variables

```javascript
import { useState } from 'react';

function Form() {
  const [name, setName] = useState("");
  const [email, setEmail] = useState("");
  const [age, setAge] = useState(0);

  return (
    <div>
      <input 
        value={name} 
        onChange={(e) => setName(e.target.value)}
        placeholder="Name"
      />
      <input 
        value={email} 
        onChange={(e) => setEmail(e.target.value)}
        placeholder="Email"
      />
      <input 
        value={age} 
        onChange={(e) => setAge(e.target.value)}
        placeholder="Age"
        type="number"
      />
    </div>
  );
}
```

### State with Objects

```javascript
import { useState } from 'react';

function UserProfile() {
  const [user, setUser] = useState({
    name: "John",
    age: 30,
    city: "New York"
  });

  // Update one property
  const updateName = (newName) => {
    setUser({
      ...user,
      name: newName
    });
  };

  return (
    <div>
      <p>Name: {user.name}</p>
      <p>Age: {user.age}</p>
      <p>City: {user.city}</p>
      <button onClick={() => updateName("Alice")}>
        Change Name
      </button>
    </div>
  );
}
```

---

## Hooks

Hooks are special functions that let you use React features in functional components.

### useState Hook

```javascript
import { useState } from 'react';

function Toggle() {
  const [isOn, setIsOn] = useState(false);

  return (
    <div>
      <p>Light is {isOn ? "ON" : "OFF"}</p>
      <button onClick={() => setIsOn(!isOn)}>
        Toggle
      </button>
    </div>
  );
}
```

### useEffect Hook

useEffect runs code after the component renders. Use it for fetching data, setting up timers, etc.

```javascript
import { useState, useEffect } from 'react';

function DataFetcher() {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);

  // Run once when component mounts
  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(response => response.json())
      .then(data => {
        setData(data);
        setLoading(false);
      });
  }, []); // Empty dependency array = run once

  if (loading) return <p>Loading...</p>;
  return <div>{JSON.stringify(data)}</div>;
}
```

### useEffect with Dependencies

```javascript
import { useState, useEffect } from 'react';

function SearchUsers() {
  const [searchTerm, setSearchTerm] = useState("");
  const [results, setResults] = useState([]);

  // Run whenever searchTerm changes
  useEffect(() => {
    if (searchTerm.length > 0) {
      fetch(`https://api.example.com/search?q=${searchTerm}`)
        .then(response => response.json())
        .then(data => setResults(data));
    }
  }, [searchTerm]); // Dependency array

  return (
    <div>
      <input 
        value={searchTerm}
        onChange={(e) => setSearchTerm(e.target.value)}
        placeholder="Search..."
      />
      <ul>
        {results.map(result => (
          <li key={result.id}>{result.name}</li>
        ))}
      </ul>
    </div>
  );
}
```

---

## Event Handling

React events are similar to HTML events but use camelCase.

### Common Events

```javascript
function EventDemo() {
  const handleClick = () => {
    console.log("Button clicked!");
  };

  const handleChange = (e) => {
    console.log("Input value:", e.target.value);
  };

  const handleSubmit = (e) => {
    e.preventDefault(); // Prevent page reload
    console.log("Form submitted!");
  };

  return (
    <div>
      <button onClick={handleClick}>Click me</button>
      <input onChange={handleChange} />
      <form onSubmit={handleSubmit}>
        <button type="submit">Submit</button>
      </form>
    </div>
  );
}
```

### Event Object

```javascript
function InputHandler() {
  const handleChange = (e) => {
    console.log(e.target.value);      // Input value
    console.log(e.target.name);       // Input name
    console.log(e.target.checked);    // For checkboxes
  };

  return <input onChange={handleChange} />;
}
```

---

## Conditional Rendering

Show or hide components based on conditions.

### If-Else

```javascript
function LoginStatus({ isLoggedIn }) {
  if (isLoggedIn) {
    return <p>Welcome back!</p>;
  } else {
    return <p>Please log in</p>;
  }
}
```

### Ternary Operator

```javascript
function LoginStatus({ isLoggedIn }) {
  return (
    <p>
      {isLoggedIn ? "Welcome back!" : "Please log in"}
    </p>
  );
}
```

### Logical AND (&&)

```javascript
function Notification({ hasMessages, messageCount }) {
  return (
    <div>
      {hasMessages && <p>You have {messageCount} messages</p>}
    </div>
  );
}
```

### Switch Statement

```javascript
function UserRole({ role }) {
  switch(role) {
    case "admin":
      return <p>Admin Panel</p>;
    case "user":
      return <p>User Dashboard</p>;
    default:
      return <p>Guest View</p>;
  }
}
```

---

## Lists and Keys

Render lists of items efficiently.

### Rendering Lists

```javascript
function FruitList() {
  const fruits = ["apple", "banana", "orange"];

  return (
    <ul>
      {fruits.map((fruit, index) => (
        <li key={index}>{fruit}</li>
      ))}
    </ul>
  );
}
```

### Lists with Objects

```javascript
function UserList() {
  const users = [
    { id: 1, name: "Alice" },
    { id: 2, name: "Bob" },
    { id: 3, name: "Charlie" }
  ];

  return (
    <ul>
      {users.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```

### Why Keys Matter

```javascript
// ❌ Bad - using index as key (can cause bugs)
{items.map((item, index) => (
  <li key={index}>{item.name}</li>
))}

// ✅ Good - using unique ID
{items.map(item => (
  <li key={item.id}>{item.name}</li>
))}
```

---

## Forms

Handling form inputs in React.

### Controlled Components

```javascript
import { useState } from 'react';

function LoginForm() {
  const [email, setEmail] = useState("");
  const [password, setPassword] = useState("");

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log("Email:", email);
    console.log("Password:", password);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="email"
        value={email}
        onChange={(e) => setEmail(e.target.value)}
        placeholder="Email"
      />
      <input
        type="password"
        value={password}
        onChange={(e) => setPassword(e.target.value)}
        placeholder="Password"
      />
      <button type="submit">Login</button>
    </form>
  );
}
```

### Form with Multiple Inputs

```javascript
import { useState } from 'react';

function SignupForm() {
  const [formData, setFormData] = useState({
    username: "",
    email: "",
    password: "",
    agreeToTerms: false
  });

  const handleChange = (e) => {
    const { name, value, type, checked } = e.target;
    setFormData({
      ...formData,
      [name]: type === 'checkbox' ? checked : value
    });
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log(formData);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        name="username"
        value={formData.username}
        onChange={handleChange}
        placeholder="Username"
      />
      <input
        name="email"
        type="email"
        value={formData.email}
        onChange={handleChange}
        placeholder="Email"
      />
      <input
        name="password"
        type="password"
        value={formData.password}
        onChange={handleChange}
        placeholder="Password"
      />
      <label>
        <input
          name="agreeToTerms"
          type="checkbox"
          checked={formData.agreeToTerms}
          onChange={handleChange}
        />
        I agree to terms
      </label>
      <button type="submit">Sign Up</button>
    </form>
  );
}
```

---

## Best Practices

### 1. Keep Components Small

```javascript
// ❌ Too big - do too many things
function Dashboard() {
  // 200 lines of code...
}

// ✅ Better - split into smaller components
function Dashboard() {
  return (
    <div>
      <Header />
      <Sidebar />
      <MainContent />
      <Footer />
    </div>
  );
}
```

### 2. Use Meaningful Names

```javascript
// ❌ Unclear
function D({ u }) {
  return <p>{u}</p>;
}

// ✅ Clear
function UserProfile({ user }) {
  return <p>{user}</p>;
}
```

### 3. Lift State Up

```javascript
// ❌ State in both components
function Parent() {
  return (
    <div>
      <Child1 />
      <Child2 />
    </div>
  );
}

// ✅ State in parent, pass to children
function Parent() {
  const [sharedData, setSharedData] = useState("");
  
  return (
    <div>
      <Child1 data={sharedData} />
      <Child2 data={sharedData} />
    </div>
  );
}
```

### 4. Avoid Inline Functions in JSX

```javascript
// ❌ Creates new function on every render
<button onClick={() => handleClick()}>Click</button>

// ✅ Better
const handleClick = () => { /* ... */ };
<button onClick={handleClick}>Click</button>
```

### 5. Use Fragment for Multiple Elements

```javascript
// ❌ Extra div in DOM
function List() {
  return (
    <div>
      <h1>Title</h1>
      <ul>...</ul>
    </div>
  );
}

// ✅ No extra div
function List() {
  return (
    <>
      <h1>Title</h1>
      <ul>...</ul>
    </>
  );
}
```

---

## Quick Reference

| Concept | Example |
|---------|---------|
| Component | `function MyComponent() { return <div>...</div>; }` |
| Props | `<Card title="Hello" />` |
| State | `const [count, setCount] = useState(0);` |
| Event | `<button onClick={handleClick}>Click</button>` |
| Conditional | `{isLoggedIn && <Dashboard />}` |
| List | `{items.map(item => <li key={item.id}>{item.name}</li>)}` |
| Form | `<input value={name} onChange={(e) => setName(e.target.value)} />` |

