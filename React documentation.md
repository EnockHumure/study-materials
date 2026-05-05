# 📚 Complete React Guide — Library Borrowing System
### Everything You Need to Understand React for This Project and Beyond

---

## 📋 TABLE OF CONTENTS

1. [What is React? Why Use It?](#1-what-is-react)
2. [How React Works — The Mental Model](#2-how-react-works)
3. [JSX — HTML Inside JavaScript](#3-jsx)
4. [Components — The Building Blocks](#4-components)
5. [Props — Passing Data Between Components](#5-props)
6. [useState — Making Things Change](#6-usestate)
7. [useEffect — Side Effects & API Calls](#7-useeffect)
8. [Event Handling — Responding to User Actions](#8-events)
9. [Forms & Controlled Inputs](#9-forms)
10. [Lists & the key Prop](#10-lists)
11. [Conditional Rendering](#11-conditional-rendering)
12. [Fetching Data from an API](#12-fetching-data)
13. [Project Structure Explained](#13-project-structure)
14. [Complete Code Walkthrough](#14-code-walkthrough)

---

## 1. What is React?

React is a JavaScript **library** for building user interfaces.

Before React, if you wanted to update a webpage after a button click, you had to:
1. Find the element in the DOM (`document.getElementById(...)`)
2. Manually change its content
3. Remember everything that needs to update
4. Keep it all in sync

React automates all of this. You describe **what the UI should look like** based on your data, and React figures out how to update the browser.

### The Core Idea:

```
Data (State)  →  React  →  What you see on screen (UI)

When data changes → React automatically updates the screen
```

**Real-life analogy:** Think of React like a smart mirror.
You just change your outfit (data), and the mirror (React) instantly shows you how you look (UI). You don't manually repaint the mirror.

---

## 2. How React Works — The Mental Model

### The Virtual DOM

React keeps a lightweight copy of the webpage (called the **Virtual DOM**) in memory.

```
Step 1: You change data (state)
Step 2: React re-renders component in Virtual DOM
Step 3: React compares new Virtual DOM vs old Virtual DOM
Step 4: React ONLY updates what actually changed in the real browser
```

This is why React is fast — it never touches the DOM more than necessary.

### Components Are Functions

In modern React, every component is just a **JavaScript function** that returns UI (JSX).

```javascript
function MyComponent() {
    return <h1>Hello World</h1>;  // returns JSX (looks like HTML)
}
```

When React needs to display this component, it **calls the function** and uses the returned JSX to build the UI.

### The Re-render Cycle

```
User does something
    → state changes (via useState)
    → React calls your function again
    → New JSX is returned
    → React updates only what changed on screen
```

This happens very fast (usually < 16ms).

---

## 3. JSX — HTML Inside JavaScript

JSX stands for **JavaScript XML**. It lets you write HTML-like syntax inside JavaScript.

```jsx
// This looks like HTML but it's actually JSX
const element = <h1 className="title">Hello, Library!</h1>;

// JSX gets compiled to this by Babel (you never write this manually)
const element = React.createElement("h1", { className: "title" }, "Hello, Library!");
```

### JSX Rules You MUST Know:

```jsx
// ✅ RULE 1: Return ONE root element (wrap in a div or <>)
function Good() {
    return (
        <div>
            <h1>Title</h1>
            <p>Paragraph</p>
        </div>
    );
}

// ✅ Or use Fragment shorthand <> </> (no extra div in the DOM)
function AlsoGood() {
    return (
        <>
            <h1>Title</h1>
            <p>Paragraph</p>
        </>
    );
}

// ❌ WRONG — two root elements, will crash
function Bad() {
    return (
        <h1>Title</h1>
        <p>Paragraph</p>   // Error!
    );
}

// ✅ RULE 2: Use className, not class (class is a reserved word in JS)
<div className="my-class">...</div>    // ✅ correct
<div class="my-class">...</div>        // ❌ wrong in JSX

// ✅ RULE 3: Close ALL tags (even self-closing ones)
<input type="text" />      // ✅ note the /
<br />                     // ✅
<img src="x.jpg" />        // ✅

// ✅ RULE 4: JavaScript expressions go inside { }
const name = "Alice";
const age = 20;
return <h1>Hello {name}, you are {age} years old</h1>;

// ✅ RULE 5: Can use ternary, but NOT if/else directly
return <p>{isAvailable ? "Available" : "Not Available"}</p>;  // ✅
// return <p>{if (x) "yes"}</p>;  // ❌ can't use if directly in JSX
```

---

## 4. Components — The Building Blocks

A component is a **reusable piece of UI**. Think of it like a LEGO brick.

```jsx
// ✅ Functional Component (modern React — this is what we use)
function BookCard({ title, author, available }) {
    return (
        <div className="book-card">
            <h3>{title}</h3>
            <p>Author: {author}</p>
            <span>{available ? "✅ Available" : "❌ Borrowed"}</span>
        </div>
    );
}

// Using the component (like an HTML tag)
function App() {
    return (
        <div>
            <BookCard title="Clean Code" author="Robert Martin" available={true} />
            <BookCard title="The Pragmatic Programmer" author="Hunt & Thomas" available={false} />
        </div>
    );
}
```

### Component Naming Rules:
- Always **PascalCase** (starts with capital letter): `BookCard`, `BorrowForm`
- Lowercase names (`bookCard`) are treated as HTML tags, not components

### File Organization:
```
src/
  components/
    BookCard.jsx        ← One component per file (common practice)
    BorrowForm.jsx
  pages/
    BooksPage.jsx       ← Page-level components
    BorrowPage.jsx
  App.jsx               ← Root component
  main.jsx              ← Entry point (renders App into the DOM)
```

---

## 5. Props — Passing Data Between Components

**Props** (properties) are how you pass data **from a parent to a child** component.

```jsx
// PARENT sends data as attributes
function BooksPage() {
    const book = { title: "React Mastery", author: "Dan Abramov" };
    
    return (
        <BookCard
            title={book.title}          // ← prop named "title"
            author={book.author}        // ← prop named "author"
            available={true}            // ← prop named "available"
            onDelete={handleDelete}     // ← you can pass FUNCTIONS too!
        />
    );
}

// CHILD receives props as a single object parameter
function BookCard(props) {
    return <h3>{props.title} by {props.author}</h3>;
}

// Better: destructure props directly (cleaner code)
function BookCard({ title, author, available, onDelete }) {
    return (
        <div>
            <h3>{title} by {author}</h3>
            <span>{available ? "Available" : "Borrowed"}</span>
            <button onClick={onDelete}>Delete</button>
        </div>
    );
}
```

### Props are READ-ONLY

```jsx
// ❌ WRONG — never mutate props!
function BookCard({ title }) {
    title = title.toUpperCase();  // BAD! Don't modify props
    return <h3>{title}</h3>;
}

// ✅ CORRECT — create a local variable
function BookCard({ title }) {
    const displayTitle = title.toUpperCase();  // OK: new local variable
    return <h3>{displayTitle}</h3>;
}
```

### Passing Functions as Props (Lifting State Up):

```jsx
// Parent manages the state and passes handler to child
function BooksPage() {
    const [books, setBooks] = useState([]);
    
    // This function lives in parent (it modifies parent's state)
    function handleDeleteBook(id) {
        setBooks(books.filter(book => book.id !== id));
    }
    
    return (
        <BookList books={books} onDelete={handleDeleteBook} />
    );
}

// Child just calls the function — doesn't need to know how it works
function BookList({ books, onDelete }) {
    return books.map(book => (
        <div key={book.id}>
            <span>{book.title}</span>
            <button onClick={() => onDelete(book.id)}>Delete</button>
        </div>
    ));
}
```

---

## 6. useState — Making Things Change

`useState` is a **Hook** that lets your component remember and change values.

```jsx
import { useState } from 'react';

function Counter() {
    // useState returns: [currentValue, functionToChangeValue]
    const [count, setCount] = useState(0);  // 0 is the initial value
    //     ↑          ↑
    // read value    update function

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>+</button>
            <button onClick={() => setCount(count - 1)}>-</button>
            <button onClick={() => setCount(0)}>Reset</button>
        </div>
    );
}
```

### The MOST IMPORTANT useState Rule:

**NEVER mutate state directly. Always use the setter function.**

```jsx
const [books, setBooks] = useState([]);

// ❌ WRONG — direct mutation, React won't re-render!
books.push({ title: "New Book" });     // React can't detect this!

// ✅ CORRECT — create a new array
setBooks([...books, { title: "New Book" }]);   // Spread old + add new

// ❌ WRONG — mutating an existing object
books[0].title = "Changed";   // React won't see this change!

// ✅ CORRECT — create a new object with the change
setBooks(books.map(book =>
    book.id === 1 ? { ...book, title: "Changed" } : book
));

// ❌ WRONG — deleting by mutation
books.splice(0, 1);   // React won't re-render

// ✅ CORRECT — filter creates a new array
setBooks(books.filter(book => book.id !== 1));
```

### useState with Objects (Forms):

```jsx
// Managing a form with one useState
function AddBookForm() {
    const [formData, setFormData] = useState({
        title: "",
        author: "",
        category: "",
        available: true
    });

    // Generic handler for all inputs
    function handleChange(e) {
        const { name, value, type, checked } = e.target;
        setFormData({
            ...formData,                           // copy all existing fields
            [name]: type === "checkbox" ? checked : value  // update just this field
        });
    }

    return (
        <form>
            <input
                name="title"           // name must match the key in formData
                value={formData.title}
                onChange={handleChange}
            />
            <input
                name="author"
                value={formData.author}
                onChange={handleChange}
            />
        </form>
    );
}
```

---

## 7. useEffect — Side Effects & API Calls

`useEffect` runs code **after** the component renders. It's used for:
- Fetching data from an API
- Setting up subscriptions
- Updating the document title
- Any code that interacts with the "outside world"

```jsx
import { useState, useEffect } from 'react';

function BooksPage() {
    const [books, setBooks] = useState([]);

    // Basic useEffect syntax:
    useEffect(() => {
        // This runs AFTER the component renders
        fetchBooks();
    }, []);  // ← dependency array
    //  ↑
    // [] = run once when component first appears (mounts)
```

### The Dependency Array — The Most Confusing Part:

```jsx
// Case 1: Empty array [] — runs ONCE when component mounts
useEffect(() => {
    fetchBooks();
}, []);

// Case 2: No array — runs after EVERY render (usually a bug/infinite loop)
useEffect(() => {
    fetchBooks();   // ⚠️ dangerous — runs too often
});

// Case 3: With values — runs when those values change
useEffect(() => {
    fetchBooksByCategory(selectedCategory);
}, [selectedCategory]);   // re-runs when selectedCategory changes

// Case 4: Multiple dependencies
useEffect(() => {
    fetchBorrows(memberId, startDate);
}, [memberId, startDate]);
```

### Fetching Data Pattern (What You'll Use Most):

```jsx
function BooksPage() {
    const [books, setBooks] = useState([]);       // stores the data
    const [loading, setLoading] = useState(true); // is it loading?
    const [error, setError] = useState(null);     // any errors?

    useEffect(() => {
        // Can't make useEffect async directly — define async inside
        async function loadBooks() {
            try {
                setLoading(true);
                const response = await fetch("http://localhost:8080/api/books");
                
                if (!response.ok) {
                    throw new Error(`Server error: ${response.status}`);
                }
                
                const data = await response.json();
                setBooks(data);
            } catch (err) {
                setError(err.message);
            } finally {
                setLoading(false);
            }
        }

        loadBooks();
    }, []);  // empty array = run once on mount

    if (loading) return <p>Loading books...</p>;
    if (error)   return <p>Error: {error}</p>;

    return (
        <ul>
            {books.map(book => (
                <li key={book.id}>{book.title}</li>
            ))}
        </ul>
    );
}
```

---

## 8. Event Handling — Responding to User Actions

```jsx
// Button click
<button onClick={() => console.log("clicked!")}>Click Me</button>

// Or with a named function (cleaner for complex logic)
function handleClick() {
    console.log("clicked!");
}
<button onClick={handleClick}>Click Me</button>
//              ↑ NO parentheses — pass the function, don't call it!
//              handleClick  ✅
//              handleClick() ❌ — this calls it immediately during render

// Click with an argument — must use arrow function wrapper
<button onClick={() => handleDelete(book.id)}>Delete</button>
//      ↑ arrow function creates a new function that calls handleDelete(book.id)

// Form submit — MUST prevent default (stops page refresh)
function handleSubmit(e) {
    e.preventDefault();   // ← critical! prevents page reload
    // ... do your submit logic
}
<form onSubmit={handleSubmit}>...</form>

// Input change
function handleChange(e) {
    console.log(e.target.value);   // current input value
    console.log(e.target.name);    // input's name attribute
}
<input onChange={handleChange} />

// Common events:
// onClick        → button, div, any element
// onChange       → input, select, textarea
// onSubmit       → form
// onFocus        → when input is clicked/focused
// onBlur         → when user leaves an input
// onKeyDown      → keyboard press
```

---

## 9. Forms & Controlled Inputs

In React, forms work differently from plain HTML. We use **controlled inputs** — the input value is stored in React state and React controls what's displayed.

```jsx
// Plain HTML form (uncontrolled — browser manages value)
<input type="text" />   // browser stores the value

// React controlled input — React manages the value
<input
    type="text"
    value={name}           // React controls what's displayed
    onChange={e => setName(e.target.value)}  // Update state on change
/>
```

### Complete Form Example — Add Book:

```jsx
function AddBookForm({ onBookAdded }) {
    const [form, setForm] = useState({
        title: "",
        author: "",
        category: "",
        available: true
    });
    const [message, setMessage] = useState("");

    // Handles ALL inputs — works because each input has name= matching state key
    function handleChange(e) {
        const { name, value, type, checked } = e.target;
        setForm(prev => ({
            ...prev,
            [name]: type === "checkbox" ? checked : value
        }));
    }

    async function handleSubmit(e) {
        e.preventDefault();  // ← Stop page refresh!

        // Simple validation
        if (!form.title || !form.author) {
            setMessage("❌ Title and Author are required");
            return;
        }

        try {
            const response = await fetch("http://localhost:8080/api/books", {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify(form)
            });

            if (!response.ok) throw new Error("Failed to add book");

            const newBook = await response.json();
            setMessage("✅ Book added successfully!");
            
            // Reset form
            setForm({ title: "", author: "", category: "", available: true });
            
            // Notify parent to refresh the list
            onBookAdded(newBook);

        } catch (err) {
            setMessage(`❌ Error: ${err.message}`);
        }
    }

    return (
        <form onSubmit={handleSubmit}>
            <input
                type="text"
                name="title"
                placeholder="Book Title"
                value={form.title}
                onChange={handleChange}
            />
            <input
                type="text"
                name="author"
                placeholder="Author"
                value={form.author}
                onChange={handleChange}
            />
            <select name="category" value={form.category} onChange={handleChange}>
                <option value="">-- Select Category --</option>
                <option value="Technology">Technology</option>
                <option value="Science">Science</option>
                <option value="Literature">Literature</option>
            </select>
            <button type="submit">Add Book</button>
            {message && <p>{message}</p>}
        </form>
    );
}
```

---

## 10. Lists & the key Prop

When rendering lists in React, every item needs a unique `key` prop.

```jsx
// ✅ CORRECT — key on the outermost element
{books.map(book => (
    <div key={book.id}>          // ← key here, not deeper
        <h3>{book.title}</h3>
        <p>{book.author}</p>
    </div>
))}

// ✅ Also correct when using a component
{books.map(book => (
    <BookCard
        key={book.id}            // ← key on the component
        title={book.title}
        author={book.author}
    />
))}

// ❌ WRONG — key on inner element
{books.map(book => (
    <div>
        <h3 key={book.id}>{book.title}</h3>   // Wrong position
    </div>
))}

// ❌ AVOID — using index as key (causes bugs with reordering)
{books.map((book, index) => (
    <div key={index}>...</div>   // Only OK if list never reorders
))}
```

**Why does React need keys?** When you update a list (add/remove/reorder), React uses keys to figure out which items changed, appeared, or disappeared. Without keys, React might re-render the wrong items.

---

## 11. Conditional Rendering

Show different UI based on conditions:

```jsx
// Method 1: Ternary operator (if/else)
{isLoading ? <p>Loading...</p> : <BookList books={books} />}

// Method 2: && short-circuit (only show if true)
{error && <p className="error">{error}</p>}
{books.length === 0 && <p>No books found.</p>}

// Method 3: if/else before return (best for complex conditions)
function BooksPage() {
    if (loading) return <div className="spinner">Loading...</div>;
    if (error)   return <div className="error">Error: {error}</div>;
    if (books.length === 0) return <p>No books in library yet.</p>;
    
    return <BookList books={books} />;
}

// Method 4: Conditional className
<span className={book.available ? "badge-green" : "badge-red"}>
    {book.available ? "Available" : "Borrowed"}
</span>
```

---

## 12. Fetching Data from an API

### The fetch() Function:

```jsx
// GET request
const response = await fetch("http://localhost:8080/api/books");
const data = await response.json();

// POST request
const response = await fetch("http://localhost:8080/api/books", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ title: "...", author: "..." })
});

// DELETE request
const response = await fetch(`http://localhost:8080/api/borrows/${id}`, {
    method: "DELETE"
});
// DELETE often returns 204 No Content (no body to parse)
```

### Always Check response.ok:

```jsx
const response = await fetch("http://localhost:8080/api/books");

// response.ok is true for 200-299 status codes
if (!response.ok) {
    throw new Error(`HTTP error! status: ${response.status}`);
}

const data = await response.json();
```

### CORS — Why Your Frontend Can't Talk to Backend

When your React app (port 3000) calls your Spring Boot API (port 8080), the browser blocks it by default. This is CORS (Cross-Origin Resource Sharing).

**Fix in Spring Boot:**
```java
@CrossOrigin(origins = "http://localhost:5173")  // Vite's port
@RestController
public class BookController { ... }

// OR globally in a config class:
@Configuration
public class CorsConfig implements WebMvcConfigurer {
    @Override
    public void addCorsMappings(CorsRegistry registry) {
        registry.addMapping("/api/**")
                .allowedOrigins("http://localhost:5173")
                .allowedMethods("GET","POST","PUT","DELETE");
    }
}
```

---

## 13. Project Structure Explained

```
library-app/
├── public/
│   └── index.html          ← The ONE HTML file. React injects into <div id="root">
├── src/
│   ├── main.jsx            ← Entry point: renders <App /> into #root
│   ├── App.jsx             ← Root component: routing/navigation between pages
│   ├── App.css             ← Global styles
│   │
│   ├── services/
│   │   └── api.js          ← ALL fetch calls in one place (clean separation)
│   │
│   ├── components/
│   │   ├── BookCard.jsx    ← Reusable book display card
│   │   ├── BookForm.jsx    ← Form to add a new book
│   │   ├── BorrowForm.jsx  ← Form to borrow a book
│   │   └── BorrowTable.jsx ← Table of borrow records
│   │
│   └── pages/
│       ├── BooksPage.jsx   ← Combines BookCard + BookForm
│       └── BorrowsPage.jsx ← Combines BorrowForm + BorrowTable
│
├── package.json            ← Project config + dependencies
└── vite.config.js          ← Build tool config (Vite)
```

---

## 14. Complete Code Walkthrough

This section explains EVERY file in the project and WHY each decision was made.

### main.jsx — Where Everything Starts

```jsx
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import './App.css'
import App from './App.jsx'

// Find the <div id="root"> in public/index.html
// Render our App component inside it
createRoot(document.getElementById('root')).render(
  <StrictMode>
    <App />
  </StrictMode>
)

// StrictMode: in development, runs effects twice to catch bugs
// You might see useEffect run twice — that's normal in development!
```

### services/api.js — Centralized API Calls

```javascript
// WHY have this file? 
// Instead of writing fetch("http://localhost:8080/api/books") in 5 different places,
// we write it ONCE here. If the URL changes, you only fix it in ONE place.

const BASE_URL = "http://localhost:8080/api";

// ===== BOOKS =====

export async function getAllBooks() {
    const res = await fetch(`${BASE_URL}/books`);
    if (!res.ok) throw new Error("Failed to fetch books");
    return res.json();
}

export async function getBookById(id) {
    const res = await fetch(`${BASE_URL}/books/${id}`);
    if (!res.ok) throw new Error(`Book ${id} not found`);
    return res.json();
}

export async function addBook(bookData) {
    const res = await fetch(`${BASE_URL}/books`, {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(bookData)
    });
    if (!res.ok) throw new Error("Failed to add book");
    return res.json();  // returns the created book with its new ID
}

export async function updateBook(id, bookData) {
    const res = await fetch(`${BASE_URL}/books/${id}`, {
        method: "PUT",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(bookData)
    });
    if (!res.ok) throw new Error("Failed to update book");
    return res.json();
}

// ===== BORROWS =====

export async function getAllBorrows() {
    const res = await fetch(`${BASE_URL}/borrows`);
    if (!res.ok) throw new Error("Failed to fetch borrows");
    return res.json();
}

export async function createBorrow(borrowData) {
    const res = await fetch(`${BASE_URL}/borrows`, {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(borrowData)
    });
    if (!res.ok) throw new Error("Failed to create borrow record");
    return res.json();
}

export async function deleteBorrow(id) {
    const res = await fetch(`${BASE_URL}/borrows/${id}`, {
        method: "DELETE"
    });
    // DELETE returns 204 No Content — no body to parse
    if (!res.ok) throw new Error("Failed to delete borrow record");
    // Don't call res.json() for 204 responses
}
```

---

That covers every React concept you need for this project and most React projects you'll build in future!

The key takeaways:
- **useState** = remember and change data
- **useEffect** = run code after render (especially API calls)  
- **Props** = pass data from parent to child
- **Controlled inputs** = React owns the form values
- **key prop** = required on every list item
- **Never mutate state** = always use the setter function
- **async/await** = the modern way to call APIs
