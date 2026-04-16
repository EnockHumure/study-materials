# JavaScript Fundamentals - Complete Beginner's Guide

## Table of Contents
1. [Introduction](#introduction)
2. [Variables and Data Types](#variables-and-data-types)
3. [Operators](#operators)
4. [Control Flow](#control-flow)
5. [Functions](#functions)
6. [Arrays](#arrays)
7. [Objects](#objects)
8. [DOM Manipulation](#dom-manipulation)
9. [Events](#events)
10. [Asynchronous JavaScript](#asynchronous-javascript)
11. [ES6+ Features](#es6-features)
12. [Best Practices](#best-practices)

---

## Introduction

JavaScript is a versatile programming language that runs in web browsers and on servers (Node.js). It makes websites interactive and dynamic.

### How to Run JavaScript
- **In Browser**: Use browser console (F12 → Console tab)
- **In HTML**: Use `<script>` tags
- **External File**: Link with `<script src="script.js"></script>`

---

## Variables and Data Types

### Declaring Variables

```javascript
// var - old way (avoid using)
var oldWay = "not recommended";

// let - for values that change
let age = 25;
age = 26; // can be reassigned

// const - for values that don't change
const PI = 3.14159;
// PI = 3.14; // Error! Cannot reassign
```

### Data Types

```javascript
// 1. String - text data
let name = "John";
let greeting = 'Hello';
let template = `My name is ${name}`; // Template literal

// 2. Number - integers and decimals
let integer = 42;
let decimal = 3.14;
let negative = -10;

// 3. Boolean - true or false
let isActive = true;
let isLoggedIn = false;

// 4. Undefined - variable declared but not assigned
let notAssigned;
console.log(notAssigned); // undefined

// 5. Null - intentional absence of value
let emptyValue = null;

// 6. Object - collection of key-value pairs
let person = {
  name: "Alice",
  age: 30
};

// 7. Array - ordered list of values
let colors = ["red", "green", "blue"];

// Check data type
console.log(typeof name); // "string"
console.log(typeof age); // "number"
```

---

## Operators

### Arithmetic Operators

```javascript
let a = 10;
let b = 3;

console.log(a + b);  // 13 - Addition
console.log(a - b);  // 7  - Subtraction
console.log(a * b);  // 30 - Multiplication
console.log(a / b);  // 3.333... - Division
console.log(a % b);  // 1  - Modulus (remainder)
console.log(a ** b); // 1000 - Exponentiation

// Increment and Decrement
let count = 5;
count++;  // count = 6
count--;  // count = 5
```

### Comparison Operators

```javascript
let x = 5;
let y = "5";

console.log(x == y);   // true - loose equality (converts types)
console.log(x === y);  // false - strict equality (checks type too)
console.log(x != y);   // false - loose inequality
console.log(x !== y);  // true - strict inequality

console.log(x > 3);    // true
console.log(x < 10);   // true
console.log(x >= 5);   // true
console.log(x <= 4);   // false
```

### Logical Operators

```javascript
let isAdult = true;
let hasLicense = false;

// AND - both must be true
console.log(isAdult && hasLicense); // false

// OR - at least one must be true
console.log(isAdult || hasLicense); // true

// NOT - inverts boolean
console.log(!isAdult); // false
```

---

## Control Flow

### If-Else Statements

```javascript
let age = 18;

if (age >= 18) {
  console.log("You are an adult");
} else if (age >= 13) {
  console.log("You are a teenager");
} else {
  console.log("You are a child");
}

// Ternary operator (shorthand)
let status = age >= 18 ? "adult" : "minor";
```

### Switch Statement

```javascript
let day = "Monday";

switch (day) {
  case "Monday":
    console.log("Start of the week");
    break;
  case "Friday":
    console.log("Almost weekend!");
    break;
  case "Saturday":
  case "Sunday":
    console.log("Weekend!");
    break;
  default:
    console.log("Midweek day");
}
```

### Loops

```javascript
// For loop
for (let i = 0; i < 5; i++) {
  console.log(i); // 0, 1, 2, 3, 4
}

// While loop
let count = 0;
while (count < 3) {
  console.log(count);
  count++;
}

// Do-While loop (runs at least once)
let num = 0;
do {
  console.log(num);
  num++;
} while (num < 3);

// For...of loop (for arrays)
let fruits = ["apple", "banana", "orange"];
for (let fruit of fruits) {
  console.log(fruit);
}

// For...in loop (for objects)
let person = { name: "John", age: 30 };
for (let key in person) {
  console.log(key + ": " + person[key]);
}
```

---

## Functions

### Function Declaration

```javascript
// Basic function
function greet(name) {
  return "Hello, " + name;
}

console.log(greet("Alice")); // "Hello, Alice"

// Function with default parameter
function multiply(a, b = 1) {
  return a * b;
}

console.log(multiply(5));    // 5
console.log(multiply(5, 3)); // 15
```

### Function Expression

```javascript
const add = function(a, b) {
  return a + b;
};

console.log(add(2, 3)); // 5
```

### Arrow Functions (ES6)

```javascript
// Concise syntax
const square = (num) => num * num;
console.log(square(4)); // 16

// Multiple parameters
const sum = (a, b) => a + b;

// Multiple lines
const greetUser = (name) => {
  let message = `Hello, ${name}!`;
  return message;
};
```

### Callback Functions

```javascript
function processUser(name, callback) {
  console.log("Processing: " + name);
  callback();
}

processUser("John", function() {
  console.log("User processed!");
});
```

---

## Arrays

### Creating and Accessing Arrays

```javascript
let fruits = ["apple", "banana", "orange"];

console.log(fruits[0]);     // "apple"
console.log(fruits.length); // 3

// Modify array
fruits[1] = "mango";
console.log(fruits); // ["apple", "mango", "orange"]
```

### Array Methods

```javascript
let numbers = [1, 2, 3, 4, 5];

// Add/Remove elements
numbers.push(6);        // Add to end: [1,2,3,4,5,6]
numbers.pop();          // Remove from end: [1,2,3,4,5]
numbers.unshift(0);     // Add to start: [0,1,2,3,4,5]
numbers.shift();        // Remove from start: [1,2,3,4,5]

// Find elements
console.log(numbers.indexOf(3));     // 2
console.log(numbers.includes(4));    // true

// Transform arrays
let doubled = numbers.map(num => num * 2);
console.log(doubled); // [2, 4, 6, 8, 10]

let evens = numbers.filter(num => num % 2 === 0);
console.log(evens); // [2, 4]

let sum = numbers.reduce((total, num) => total + num, 0);
console.log(sum); // 15

// Iterate
numbers.forEach(num => console.log(num));

// Sort and reverse
let letters = ["c", "a", "b"];
letters.sort();    // ["a", "b", "c"]
letters.reverse(); // ["c", "b", "a"]

// Slice and splice
let sliced = numbers.slice(1, 3);  // [2, 3] - doesn't modify original
numbers.splice(2, 1, 99);          // Remove 1 at index 2, add 99
```

---

## Objects

### Creating Objects

```javascript
// Object literal
let person = {
  firstName: "John",
  lastName: "Doe",
  age: 30,
  isEmployed: true,
  greet: function() {
    return "Hello, I'm " + this.firstName;
  }
};

// Accessing properties
console.log(person.firstName);      // "John" - dot notation
console.log(person["lastName"]);    // "Doe" - bracket notation

// Calling methods
console.log(person.greet()); // "Hello, I'm John"

// Adding properties
person.email = "john@example.com";

// Deleting properties
delete person.age;
```

### Object Methods

```javascript
let user = {
  name: "Alice",
  age: 25,
  city: "New York"
};

// Get all keys
console.log(Object.keys(user)); // ["name", "age", "city"]

// Get all values
console.log(Object.values(user)); // ["Alice", 25, "New York"]

// Get key-value pairs
console.log(Object.entries(user)); 
// [["name", "Alice"], ["age", 25], ["city", "New York"]]

// Copy object
let userCopy = Object.assign({}, user);
let userCopy2 = { ...user }; // Spread operator (ES6)
```

### Destructuring

```javascript
let person = { name: "Bob", age: 30, city: "LA" };

// Extract properties
let { name, age } = person;
console.log(name); // "Bob"
console.log(age);  // 30

// Array destructuring
let colors = ["red", "green", "blue"];
let [first, second] = colors;
console.log(first);  // "red"
console.log(second); // "green"
```

---

## DOM Manipulation

### Selecting Elements

```javascript
// Select by ID
let header = document.getElementById("header");

// Select by class (returns first match)
let button = document.querySelector(".btn");

// Select all by class
let buttons = document.querySelectorAll(".btn");

// Select by tag
let paragraphs = document.getElementsByTagName("p");
```

### Modifying Elements

```javascript
// Change text content
let heading = document.getElementById("title");
heading.textContent = "New Title";
heading.innerText = "Another Title";

// Change HTML content
let container = document.getElementById("container");
container.innerHTML = "<p>New paragraph</p>";

// Change attributes
let image = document.querySelector("img");
image.src = "new-image.jpg";
image.alt = "Description";
image.setAttribute("data-id", "123");

// Change styles
let box = document.getElementById("box");
box.style.color = "blue";
box.style.backgroundColor = "yellow";
box.style.fontSize = "20px";

// Add/Remove classes
box.classList.add("active");
box.classList.remove("hidden");
box.classList.toggle("highlight");
console.log(box.classList.contains("active")); // true
```

### Creating and Removing Elements

```javascript
// Create new element
let newDiv = document.createElement("div");
newDiv.textContent = "I'm a new div";
newDiv.className = "box";

// Add to DOM
document.body.appendChild(newDiv);

// Insert before another element
let parent = document.getElementById("parent");
let child = document.getElementById("child");
parent.insertBefore(newDiv, child);

// Remove element
let elementToRemove = document.getElementById("old");
elementToRemove.remove();
```

---

## Events

### Adding Event Listeners

```javascript
// Click event
let button = document.getElementById("myButton");
button.addEventListener("click", function() {
  console.log("Button clicked!");
});

// With arrow function
button.addEventListener("click", () => {
  console.log("Button clicked!");
});

// Event object
button.addEventListener("click", (event) => {
  console.log(event.target); // The clicked element
  console.log(event.type);   // "click"
});
```

### Common Events

```javascript
// Mouse events
element.addEventListener("click", handleClick);
element.addEventListener("dblclick", handleDoubleClick);
element.addEventListener("mouseenter", handleMouseEnter);
element.addEventListener("mouseleave", handleMouseLeave);

// Keyboard events
document.addEventListener("keydown", (e) => {
  console.log("Key pressed: " + e.key);
});

document.addEventListener("keyup", (e) => {
  console.log("Key released: " + e.key);
});

// Form events
let form = document.getElementById("myForm");
form.addEventListener("submit", (e) => {
  e.preventDefault(); // Prevent form submission
  console.log("Form submitted");
});

let input = document.getElementById("myInput");
input.addEventListener("input", (e) => {
  console.log("Input value: " + e.target.value);
});

input.addEventListener("focus", () => {
  console.log("Input focused");
});

input.addEventListener("blur", () => {
  console.log("Input lost focus");
});
```

### Event Delegation

```javascript
// Handle events on dynamically created elements
let list = document.getElementById("list");

list.addEventListener("click", (e) => {
  if (e.target.tagName === "LI") {
    console.log("List item clicked: " + e.target.textContent);
  }
});
```

---

## Asynchronous JavaScript

### setTimeout and setInterval

```javascript
// Execute once after delay
setTimeout(() => {
  console.log("Executed after 2 seconds");
}, 2000);

// Execute repeatedly
let intervalId = setInterval(() => {
  console.log("Executed every 1 second");
}, 1000);

// Stop interval
clearInterval(intervalId);
```

### Promises

```javascript
// Creating a promise
let myPromise = new Promise((resolve, reject) => {
  let success = true;
  
  if (success) {
    resolve("Operation successful!");
  } else {
    reject("Operation failed!");
  }
});

// Using a promise
myPromise
  .then(result => {
    console.log(result); // "Operation successful!"
  })
  .catch(error => {
    console.log(error);
  })
  .finally(() => {
    console.log("Promise completed");
  });

// Chaining promises
fetch("https://api.example.com/data")
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error("Error:", error));
```

### Async/Await

```javascript
// Async function
async function fetchData() {
  try {
    let response = await fetch("https://api.example.com/data");
    let data = await response.json();
    console.log(data);
    return data;
  } catch (error) {
    console.error("Error:", error);
  }
}

fetchData();

// Multiple async operations
async function getMultipleData() {
  try {
    let [users, posts] = await Promise.all([
      fetch("/api/users").then(r => r.json()),
      fetch("/api/posts").then(r => r.json())
    ]);
    
    console.log(users, posts);
  } catch (error) {
    console.error(error);
  }
}
```

---

## ES6+ Features

### Template Literals

```javascript
let name = "Alice";
let age = 25;

// Old way
let message1 = "My name is " + name + " and I'm " + age + " years old";

// Template literal
let message2 = `My name is ${name} and I'm ${age} years old`;

// Multi-line strings
let html = `
  <div>
    <h1>${name}</h1>
    <p>Age: ${age}</p>
  </div>
`;
```

### Spread Operator

```javascript
// Arrays
let arr1 = [1, 2, 3];
let arr2 = [4, 5, 6];
let combined = [...arr1, ...arr2]; // [1, 2, 3, 4, 5, 6]

// Objects
let person = { name: "John", age: 30 };
let employee = { ...person, job: "Developer" };
// { name: "John", age: 30, job: "Developer" }

// Function arguments
let numbers = [1, 2, 3, 4, 5];
console.log(Math.max(...numbers)); // 5
```

### Rest Parameters

```javascript
function sum(...numbers) {
  return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3, 4)); // 10
```

### Default Parameters

```javascript
function greet(name = "Guest", greeting = "Hello") {
  return `${greeting}, ${name}!`;
}

console.log(greet());              // "Hello, Guest!"
console.log(greet("Alice"));       // "Hello, Alice!"
console.log(greet("Bob", "Hi"));   // "Hi, Bob!"
```

### Classes

```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  
  greet() {
    return `Hello, I'm ${this.name}`;
  }
  
  static species() {
    return "Homo sapiens";
  }
}

let person = new Person("Alice", 30);
console.log(person.greet()); // "Hello, I'm Alice"
console.log(Person.species()); // "Homo sapiens"

// Inheritance
class Employee extends Person {
  constructor(name, age, job) {
    super(name, age);
    this.job = job;
  }
  
  work() {
    return `${this.name} is working as a ${this.job}`;
  }
}

let emp = new Employee("Bob", 25, "Developer");
console.log(emp.greet()); // "Hello, I'm Bob"
console.log(emp.work());  // "Bob is working as a Developer"
```

### Modules

```javascript
// math.js - Export
export const PI = 3.14159;
export function add(a, b) {
  return a + b;
}
export default function multiply(a, b) {
  return a * b;
}

// main.js - Import
import multiply, { PI, add } from './math.js';
console.log(PI);           // 3.14159
console.log(add(2, 3));    // 5
console.log(multiply(4, 5)); // 20
```

---

## Best Practices

### 1. Use Strict Mode

```javascript
"use strict";
// Catches common coding mistakes
```

### 2. Use const and let, Avoid var

```javascript
// Good
const MAX_SIZE = 100;
let count = 0;

// Avoid
var oldStyle = "not recommended";
```

### 3. Use Meaningful Variable Names

```javascript
// Bad
let x = 5;
let d = new Date();

// Good
let userAge = 5;
let currentDate = new Date();
```

### 4. Use === Instead of ==

```javascript
// Bad
if (value == "5") { }

// Good
if (value === "5") { }
```

### 5. Handle Errors Properly

```javascript
try {
  // Code that might throw an error
  let data = JSON.parse(jsonString);
} catch (error) {
  console.error("Error parsing JSON:", error);
} finally {
  console.log("Cleanup code here");
}
```

### 6. Keep Functions Small and Focused

```javascript
// Each function should do one thing well
function calculateTotal(items) {
  return items.reduce((sum, item) => sum + item.price, 0);
}

function applyDiscount(total, discountPercent) {
  return total * (1 - discountPercent / 100);
}
```

### 7. Comment When Necessary

```javascript
// Explain WHY, not WHAT
// Calculate tax based on regional requirements (EU VAT rules)
let tax = price * 0.20;
```

### 8. Avoid Global Variables

```javascript
// Bad
let globalCounter = 0;

// Good - use modules or closures
function createCounter() {
  let count = 0;
  return {
    increment: () => ++count,
    getCount: () => count
  };
}
```

### 9. Use Array Methods Instead of Loops

```javascript
// Instead of
let doubled = [];
for (let i = 0; i < numbers.length; i++) {
  doubled.push(numbers[i] * 2);
}

// Use
let doubled = numbers.map(num => num * 2);
```

### 10. Validate User Input

```javascript
function processAge(age) {
  if (typeof age !== "number" || age < 0 || age > 150) {
    throw new Error("Invalid age");
  }
  // Process valid age
}
```

---

## Quick Reference

### Common String Methods
- `length` - Get string length
- `toUpperCase()` - Convert to uppercase
- `toLowerCase()` - Convert to lowercase
- `trim()` - Remove whitespace
- `split()` - Split into array
- `includes()` - Check if contains substring
- `slice()` - Extract portion
- `replace()` - Replace text

### Common Array Methods
- `push()` - Add to end
- `pop()` - Remove from end
- `shift()` - Remove from start
- `unshift()` - Add to start
- `map()` - Transform elements
- `filter()` - Filter elements
- `reduce()` - Reduce to single value
- `find()` - Find first match
- `forEach()` - Iterate

### Common Object Methods
- `Object.keys()` - Get keys
- `Object.values()` - Get values
- `Object.entries()` - Get key-value pairs
- `Object.assign()` - Copy/merge objects

---

## Resources for Further Learning

- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript) - Comprehensive JavaScript documentation
- [JavaScript.info](https://javascript.info/) - Modern JavaScript tutorial
- [Eloquent JavaScript](https://eloquentjavascript.net/) - Free online book
- [freeCodeCamp](https://www.freecodecamp.org/) - Interactive coding challenges

---

**Happy Coding! 🚀**
