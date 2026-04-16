# JavaScript Exercises - Beginner to Intermediate

## How to Use This Guide

1. Read the exercise description
2. Try to solve it yourself first
3. Check the solution
4. Understand why it works
5. Modify it and experiment

**Difficulty Levels:**
- 🟢 Easy - Basic concepts
- 🟡 Medium - Combines multiple concepts
- 🔴 Hard - Requires problem-solving

---

## Section 1: Variables and Data Types

### Exercise 1.1: Create and Log Variables 🟢

**Task:** Create variables for a person and log them to the console.

**Instructions:**
1. Create a variable `firstName` with your name
2. Create a variable `age` with your age
3. Create a variable `isStudent` with true or false
4. Log all three to the console

**Starter Code:**
```javascript
// Write your code here

```

**Solution:**
```javascript
let firstName = "John";
let age = 25;
let isStudent = true;

console.log(firstName);
console.log(age);
console.log(isStudent);
```

**Expected Output:**
```
John
25
true
```

---

### Exercise 1.2: String Concatenation 🟢

**Task:** Combine strings to create a sentence.

**Instructions:**
1. Create variables: `name`, `city`, `job`
2. Create a sentence combining all three
3. Log the sentence

**Starter Code:**
```javascript
let name = "Alice";
let city = "New York";
let job = "Developer";

// Create a sentence here

```

**Solution:**
```javascript
let name = "Alice";
let city = "New York";
let job = "Developer";

let sentence = name + " is a " + job + " from " + city;
console.log(sentence);

// Or using template literals (better way):
let sentence2 = `${name} is a ${job} from ${city}`;
console.log(sentence2);
```

**Expected Output:**
```
Alice is a Developer from New York
Alice is a Developer from New York
```

---

### Exercise 1.3: Data Type Checker 🟡

**Task:** Check and log the data type of different values.

**Instructions:**
1. Create variables with different data types
2. Use `typeof` to check each one
3. Log the results

**Starter Code:**
```javascript
let text = "Hello";
let number = 42;
let decimal = 3.14;
let isTrue = true;
let nothing = null;
let notAssigned;

// Check the type of each variable

```

**Solution:**
```javascript
let text = "Hello";
let number = 42;
let decimal = 3.14;
let isTrue = true;
let nothing = null;
let notAssigned;

console.log(typeof text);        // "string"
console.log(typeof number);      // "number"
console.log(typeof decimal);     // "number"
console.log(typeof isTrue);      // "boolean"
console.log(typeof nothing);     // "object" (quirk in JavaScript!)
console.log(typeof notAssigned); // "undefined"
```

---

## Section 2: Operators

### Exercise 2.1: Math Operations 🟢

**Task:** Perform basic math operations.

**Instructions:**
1. Create two variables: `a = 10` and `b = 3`
2. Calculate: addition, subtraction, multiplication, division, modulus
3. Log each result

**Starter Code:**
```javascript
let a = 10;
let b = 3;

// Calculate and log results

```

**Solution:**
```javascript
let a = 10;
let b = 3;

console.log(a + b);  // 13
console.log(a - b);  // 7
console.log(a * b);  // 30
console.log(a / b);  // 3.333...
console.log(a % b);  // 1
console.log(a ** b); // 1000
```

---

### Exercise 2.2: Comparison Operators 🟡

**Task:** Compare values and log the results.

**Instructions:**
1. Create variables: `x = 5`, `y = "5"`, `z = 10`
2. Compare them using different operators
3. Log the results and explain why

**Starter Code:**
```javascript
let x = 5;
let y = "5";
let z = 10;

// Compare and log

```

**Solution:**
```javascript
let x = 5;
let y = "5";
let z = 10;

console.log(x == y);   // true (loose equality - converts types)
console.log(x === y);  // false (strict equality - checks type)
console.log(x < z);    // true
console.log(x > z);    // false
console.log(x <= 5);   // true
console.log(x !== y);  // true (strict inequality)
```

**Key Learning:** Always use `===` instead of `==` to avoid type conversion bugs!

---

### Exercise 2.3: Logical Operators 🟡

**Task:** Use logical operators to make decisions.

**Instructions:**
1. Create variables: `age = 20`, `hasLicense = true`, `hasInsurance = false`
2. Check if person can drive (needs age >= 18 AND license)
3. Check if person can drive legally (needs license AND insurance)

**Starter Code:**
```javascript
let age = 20;
let hasLicense = true;
let hasInsurance = false;

// Check conditions

```

**Solution:**
```javascript
let age = 20;
let hasLicense = true;
let hasInsurance = false;

// Can drive (age + license)
let canDrive = age >= 18 && hasLicense;
console.log("Can drive:", canDrive); // true

// Can drive legally (license + insurance)
let canDriveLegally = hasLicense && hasInsurance;
console.log("Can drive legally:", canDriveLegally); // false

// Has either license or insurance
let hasEither = hasLicense || hasInsurance;
console.log("Has either:", hasEither); // true

// Doesn't have insurance
let noInsurance = !hasInsurance;
console.log("No insurance:", noInsurance); // true
```

---

## Section 3: Control Flow

### Exercise 3.1: If-Else Statements 🟢

**Task:** Check age and determine status.

**Instructions:**
1. Create a variable `age`
2. If age >= 18, log "Adult"
3. Else if age >= 13, log "Teenager"
4. Else log "Child"

**Starter Code:**
```javascript
let age = 15;

// Write if-else statement

```

**Solution:**
```javascript
let age = 15;

if (age >= 18) {
  console.log("Adult");
} else if (age >= 13) {
  console.log("Teenager");
} else {
  console.log("Child");
}

// Output: Teenager
```

---

### Exercise 3.2: Ternary Operator 🟡

**Task:** Use ternary operator to simplify if-else.

**Instructions:**
1. Create a variable `score = 75`
2. If score >= 60, status is "Pass", else "Fail"
3. Use ternary operator
4. Log the result

**Starter Code:**
```javascript
let score = 75;

// Use ternary operator

```

**Solution:**
```javascript
let score = 75;

let status = score >= 60 ? "Pass" : "Fail";
console.log(status); // Pass

// More complex example:
let grade = score >= 90 ? "A" : score >= 80 ? "B" : score >= 70 ? "C" : "F";
console.log(grade); // C
```

---

### Exercise 3.3: Switch Statement 🟡

**Task:** Use switch to handle multiple cases.

**Instructions:**
1. Create a variable `day = 3`
2. Use switch to log the day name (1=Monday, 2=Tuesday, etc.)
3. Add a default case

**Starter Code:**
```javascript
let day = 3;

// Write switch statement

```

**Solution:**
```javascript
let day = 3;

switch (day) {
  case 1:
    console.log("Monday");
    break;
  case 2:
    console.log("Tuesday");
    break;
  case 3:
    console.log("Wednesday");
    break;
  case 4:
    console.log("Thursday");
    break;
  case 5:
    console.log("Friday");
    break;
  case 6:
    console.log("Saturday");
    break;
  case 7:
    console.log("Sunday");
    break;
  default:
    console.log("Invalid day");
}

// Output: Wednesday
```

---

## Section 4: Loops

### Exercise 4.1: For Loop - Count to 10 🟢

**Task:** Use a for loop to count from 1 to 10.

**Instructions:**
1. Create a for loop that runs 10 times
2. Log the number each time

**Starter Code:**
```javascript
// Write for loop

```

**Solution:**
```javascript
for (let i = 1; i <= 10; i++) {
  console.log(i);
}

// Output: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10
```

---

### Exercise 4.2: For Loop - Multiplication Table 🟡

**Task:** Create a multiplication table.

**Instructions:**
1. Create a for loop from 1 to 10
2. For each number, multiply by 5
3. Log the result

**Starter Code:**
```javascript
// Create multiplication table for 5

```

**Solution:**
```javascript
for (let i = 1; i <= 10; i++) {
  console.log(`5 x ${i} = ${5 * i}`);
}

// Output:
// 5 x 1 = 5
// 5 x 2 = 10
// 5 x 3 = 15
// ... and so on
```

---

### Exercise 4.3: While Loop - Sum Numbers 🟡

**Task:** Use while loop to sum numbers.

**Instructions:**
1. Create a variable `sum = 0`
2. Create a while loop that runs while `sum < 100`
3. Add a random number (1-20) to sum each iteration
4. Log the final sum

**Starter Code:**
```javascript
let sum = 0;

// Write while loop

```

**Solution:**
```javascript
let sum = 0;
let count = 0;

while (sum < 100) {
  let randomNum = Math.floor(Math.random() * 20) + 1;
  sum += randomNum;
  count++;
  console.log(`Iteration ${count}: Added ${randomNum}, Sum = ${sum}`);
}

console.log(`Final sum: ${sum}`);
```

---

### Exercise 4.4: For...of Loop - Print Array 🟢

**Task:** Use for...of to loop through an array.

**Instructions:**
1. Create an array of fruits
2. Use for...of to print each fruit

**Starter Code:**
```javascript
let fruits = ["apple", "banana", "orange", "grape"];

// Use for...of loop

```

**Solution:**
```javascript
let fruits = ["apple", "banana", "orange", "grape"];

for (let fruit of fruits) {
  console.log(fruit);
}

// Output:
// apple
// banana
// orange
// grape
```

---

## Section 5: Functions

### Exercise 5.1: Simple Function 🟢

**Task:** Create a function that greets a person.

**Instructions:**
1. Create a function `greet` that takes a name parameter
2. Return a greeting message
3. Call the function with different names

**Starter Code:**
```javascript
// Create greet function

// Call it

```

**Solution:**
```javascript
function greet(name) {
  return "Hello, " + name + "!";
}

console.log(greet("Alice"));  // Hello, Alice!
console.log(greet("Bob"));    // Hello, Bob!
console.log(greet("Charlie")); // Hello, Charlie!
```

---

### Exercise 5.2: Function with Multiple Parameters 🟡

**Task:** Create a function that calculates area of a rectangle.

**Instructions:**
1. Create a function `calculateArea` with width and height parameters
2. Return the area (width * height)
3. Call it with different values

**Starter Code:**
```javascript
// Create calculateArea function

// Call it

```

**Solution:**
```javascript
function calculateArea(width, height) {
  return width * height;
}

console.log(calculateArea(5, 10));   // 50
console.log(calculateArea(3, 7));    // 21
console.log(calculateArea(10, 10));  // 100
```

---

### Exercise 5.3: Arrow Function 🟡

**Task:** Convert regular function to arrow function.

**Instructions:**
1. Create an arrow function `add` that takes two numbers
2. Return their sum
3. Call it

**Starter Code:**
```javascript
// Create arrow function add

// Call it

```

**Solution:**
```javascript
// Long form
const add = (a, b) => {
  return a + b;
};

// Short form (one line)
const add2 = (a, b) => a + b;

console.log(add(5, 3));   // 8
console.log(add2(10, 20)); // 30
```

---

### Exercise 5.4: Function with Default Parameter 🟡

**Task:** Create a function with default values.

**Instructions:**
1. Create a function `multiply` with parameters `a` and `b = 1`
2. Return a * b
3. Call it with and without the second parameter

**Starter Code:**
```javascript
// Create multiply function

// Call it

```

**Solution:**
```javascript
function multiply(a, b = 1) {
  return a * b;
}

console.log(multiply(5));      // 5 (b defaults to 1)
console.log(multiply(5, 3));   // 15
console.log(multiply(10, 2));  // 20
```

---

## Section 6: Arrays

### Exercise 6.1: Create and Access Array 🟢

**Task:** Create an array and access elements.

**Instructions:**
1. Create an array of 5 numbers
2. Log the first element
3. Log the last element
4. Log the length

**Starter Code:**
```javascript
let numbers = [10, 20, 30, 40, 50];

// Access and log elements

```

**Solution:**
```javascript
let numbers = [10, 20, 30, 40, 50];

console.log(numbers[0]);      // 10 (first)
console.log(numbers[4]);      // 50 (last)
console.log(numbers.length);  // 5
```

---

### Exercise 6.2: Array Methods - Add and Remove 🟡

**Task:** Use push, pop, shift, unshift methods.

**Instructions:**
1. Create an array of colors
2. Add a color to the end (push)
3. Remove from the end (pop)
4. Add to the beginning (unshift)
5. Remove from the beginning (shift)
6. Log the array after each operation

**Starter Code:**
```javascript
let colors = ["red", "blue", "green"];

// Use array methods

```

**Solution:**
```javascript
let colors = ["red", "blue", "green"];

colors.push("yellow");
console.log(colors); // ["red", "blue", "green", "yellow"]

colors.pop();
console.log(colors); // ["red", "blue", "green"]

colors.unshift("purple");
console.log(colors); // ["purple", "red", "blue", "green"]

colors.shift();
console.log(colors); // ["red", "blue", "green"]
```

---

### Exercise 6.3: Array Map Method 🟡

**Task:** Use map to transform array elements.

**Instructions:**
1. Create an array of numbers [1, 2, 3, 4, 5]
2. Use map to double each number
3. Log the new array

**Starter Code:**
```javascript
let numbers = [1, 2, 3, 4, 5];

// Use map to double numbers

```

**Solution:**
```javascript
let numbers = [1, 2, 3, 4, 5];

let doubled = numbers.map(num => num * 2);
console.log(doubled); // [2, 4, 6, 8, 10]
```

---

### Exercise 6.4: Array Filter Method 🟡

**Task:** Use filter to get specific elements.

**Instructions:**
1. Create an array of numbers [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
2. Use filter to get only even numbers
3. Log the result

**Starter Code:**
```javascript
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

// Use filter to get even numbers

```

**Solution:**
```javascript
let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

let evens = numbers.filter(num => num % 2 === 0);
console.log(evens); // [2, 4, 6, 8, 10]
```

---

### Exercise 6.5: Array Reduce Method 🔴

**Task:** Use reduce to sum all numbers.

**Instructions:**
1. Create an array of numbers [1, 2, 3, 4, 5]
2. Use reduce to sum all numbers
3. Log the result

**Starter Code:**
```javascript
let numbers = [1, 2, 3, 4, 5];

// Use reduce to sum

```

**Solution:**
```javascript
let numbers = [1, 2, 3, 4, 5];

let sum = numbers.reduce((total, num) => total + num, 0);
console.log(sum); // 15

// Breaking it down:
// total = 0, num = 1 → total = 1
// total = 1, num = 2 → total = 3
// total = 3, num = 3 → total = 6
// total = 6, num = 4 → total = 10
// total = 10, num = 5 → total = 15
```

---

## Section 7: Objects

### Exercise 7.1: Create and Access Object 🟢

**Task:** Create an object and access properties.

**Instructions:**
1. Create an object for a person with name, age, city
2. Log each property using dot notation
3. Log each property using bracket notation

**Starter Code:**
```javascript
let person = {
  name: "John",
  age: 30,
  city: "New York"
};

// Access properties

```

**Solution:**
```javascript
let person = {
  name: "John",
  age: 30,
  city: "New York"
};

// Dot notation
console.log(person.name);   // John
console.log(person.age);    // 30
console.log(person.city);   // New York

// Bracket notation
console.log(person["name"]); // John
console.log(person["age"]);  // 30
```

---

### Exercise 7.2: Object Methods 🟡

**Task:** Use Object methods to get keys and values.

**Instructions:**
1. Create an object with 3 properties
2. Use Object.keys() to get all keys
3. Use Object.values() to get all values
4. Use Object.entries() to get key-value pairs

**Starter Code:**
```javascript
let user = {
  username: "alice",
  email: "alice@example.com",
  age: 25
};

// Use Object methods

```

**Solution:**
```javascript
let user = {
  username: "alice",
  email: "alice@example.com",
  age: 25
};

console.log(Object.keys(user));
// ["username", "email", "age"]

console.log(Object.values(user));
// ["alice", "alice@example.com", 25]

console.log(Object.entries(user));
// [["username", "alice"], ["email", "alice@example.com"], ["age", 25]]
```

---

### Exercise 7.3: Object Destructuring 🟡

**Task:** Use destructuring to extract properties.

**Instructions:**
1. Create an object with name, age, city
2. Destructure to get name and age
3. Log them

**Starter Code:**
```javascript
let person = {
  name: "Bob",
  age: 28,
  city: "LA"
};

// Destructure

```

**Solution:**
```javascript
let person = {
  name: "Bob",
  age: 28,
  city: "LA"
};

// Destructure
let { name, age } = person;

console.log(name); // Bob
console.log(age);  // 28

// You can also rename
let { name: personName, age: personAge } = person;
console.log(personName); // Bob
```

---

## Section 8: Combining Everything

### Exercise 8.1: Student Grade Calculator 🔴

**Task:** Create a program that calculates student grades.

**Instructions:**
1. Create an array of student objects (name, scores)
2. For each student, calculate average score
3. Determine grade (A: 90+, B: 80+, C: 70+, D: 60+, F: <60)
4. Log results

**Starter Code:**
```javascript
let students = [
  { name: "Alice", scores: [85, 90, 88] },
  { name: "Bob", scores: [75, 80, 78] },
  { name: "Charlie", scores: [95, 92, 98] }
];

// Calculate grades

```

**Solution:**
```javascript
let students = [
  { name: "Alice", scores: [85, 90, 88] },
  { name: "Bob", scores: [75, 80, 78] },
  { name: "Charlie", scores: [95, 92, 98] }
];

students.forEach(student => {
  // Calculate average
  let average = student.scores.reduce((sum, score) => sum + score, 0) / student.scores.length;
  
  // Determine grade
  let grade;
  if (average >= 90) grade = "A";
  else if (average >= 80) grade = "B";
  else if (average >= 70) grade = "C";
  else if (average >= 60) grade = "D";
  else grade = "F";
  
  console.log(`${student.name}: Average = ${average.toFixed(2)}, Grade = ${grade}`);
});

// Output:
// Alice: Average = 87.67, Grade = B
// Bob: Average = 77.67, Grade = C
// Charlie: Average = 95.00, Grade = A
```

---

### Exercise 8.2: Shopping Cart Calculator 🔴

**Task:** Create a shopping cart system.

**Instructions:**
1. Create an array of products (name, price, quantity)
2. Calculate total for each product
3. Calculate grand total
4. Apply 10% discount if total > 100
5. Log the receipt

**Starter Code:**
```javascript
let cart = [
  { name: "Laptop", price: 1000, quantity: 1 },
  { name: "Mouse", price: 25, quantity: 2 },
  { name: "Keyboard", price: 75, quantity: 1 }
];

// Calculate and display receipt

```

**Solution:**
```javascript
let cart = [
  { name: "Laptop", price: 1000, quantity: 1 },
  { name: "Mouse", price: 25, quantity: 2 },
  { name: "Keyboard", price: 75, quantity: 1 }
];

console.log("=== SHOPPING CART ===");

let grandTotal = 0;

cart.forEach(item => {
  let itemTotal = item.price * item.quantity;
  grandTotal += itemTotal;
  console.log(`${item.name}: $${item.price} x ${item.quantity} = $${itemTotal}`);
});

console.log("-------------------");
console.log(`Subtotal: $${grandTotal}`);

// Apply discount
let discount = grandTotal > 100 ? grandTotal * 0.1 : 0;
let finalTotal = grandTotal - discount;

if (discount > 0) {
  console.log(`Discount (10%): -$${discount.toFixed(2)}`);
}

console.log(`Total: $${finalTotal.toFixed(2)}`);
```

---

## Challenge Exercises

### Challenge 1: Number Guessing Game 🔴

**Task:** Create a number guessing game.

**Instructions:**
1. Generate a random number between 1-100
2. Ask user to guess (use prompt)
3. Tell if guess is too high, too low, or correct
4. Count attempts
5. Congratulate when correct

**Starter Code:**
```javascript
// Create number guessing game

```

**Solution:**
```javascript
let secretNumber = Math.floor(Math.random() * 100) + 1;
let attempts = 0;
let guessed = false;

while (!guessed) {
  let guess = prompt("Guess a number between 1-100:");
  guess = parseInt(guess);
  attempts++;
  
  if (guess === secretNumber) {
    console.log(`Correct! You guessed it in ${attempts} attempts!`);
    guessed = true;
  } else if (guess < secretNumber) {
    console.log("Too low, try again!");
  } else {
    console.log("Too high, try again!");
  }
}
```

---

### Challenge 2: To-Do List 🔴

**Task:** Create a simple to-do list.

**Instructions:**
1. Create an array to store tasks
2. Create functions to: add task, remove task, list all tasks
3. Use a loop to let user interact

**Starter Code:**
```javascript
let tasks = [];

function addTask(task) {
  // Add task
}

function removeTask(index) {
  // Remove task
}

function listTasks() {
  // List all tasks
}

// Use the functions

```

**Solution:**
```javascript
let tasks = [];

function addTask(task) {
  tasks.push(task);
  console.log(`Added: ${task}`);
}

function removeTask(index) {
  if (index >= 0 && index < tasks.length) {
    let removed = tasks.splice(index, 1);
    console.log(`Removed: ${removed[0]}`);
  }
}

function listTasks() {
  console.log("=== TO-DO LIST ===");
  tasks.forEach((task, index) => {
    console.log(`${index + 1}. ${task}`);
  });
}

// Use it
addTask("Buy groceries");
addTask("Finish homework");
addTask("Call mom");
listTasks();
removeTask(1);
listTasks();
```

---

## How to Practice

1. **Try without looking at solution** - Spend 15-30 minutes
2. **If stuck, read hints** - Don't jump to solution
3. **Check solution** - Compare with yours
4. **Understand differences** - Why is theirs different?
5. **Modify and experiment** - Change values, add features
6. **Do it again tomorrow** - Repetition helps memory

---

## Tips for Success

✅ **Type the code yourself** - Don't copy-paste
✅ **Understand each line** - Know what it does
✅ **Break it down** - Solve step by step
✅ **Test your code** - Run it and see results
✅ **Make mistakes** - That's how you learn
✅ **Google errors** - Learn to read error messages
✅ **Practice daily** - 30 minutes is better than 3 hours once a week

---

## Next Steps

After completing these exercises:
1. Move to **React Exercises**
2. Then **Tailwind Exercises**
3. Then build a **real project** combining all three

Good luck! 💪

