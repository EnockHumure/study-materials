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

**Real-Life Scenario:** Think of variables like labeled boxes in your home:
- **const** = A box with a permanent label (like your birth certificate box - the content never changes)
- **let** = A box with a changeable label (like your clothes drawer - contents change with seasons)
- **var** = An old, confusing box system (avoid it - it's like having boxes that randomly appear in different rooms)

```javascript
// const - Like your birthday, it never changes
const myBirthday = "January 15, 1995";
// myBirthday = "March 20, 2000"; // Error! You can't change your birthday!

// let - Like your age, it changes every year
let myAge = 25;
myAge = 26; // Next year, your age changes
myAge = 27; // And it keeps changing

// var - old way (avoid using)
// Like keeping important documents in random places - confusing!
var oldWay = "not recommended";
```

### Data Types

**Real-Life Scenario:** Data types are like different types of information you write down:

```javascript
// 1. STRING - Like writing someone's name on paper
// Real-life: Name tags, addresses, messages
let customerName = "Sarah Johnson";
let address = "123 Main Street";
let message = `Hello ${customerName}!`; // Like a personalized letter

// 2. NUMBER - Like counting money or measuring things
// Real-life: Prices, ages, temperatures, distances
let productPrice = 29.99;        // Price tag at a store
let temperature = -5;            // Winter temperature
let studentsInClass = 30;        // Counting people

// 3. BOOLEAN - Like a light switch (ON/OFF, YES/NO)
// Real-life: Is the door locked? Is it raining? Are you hungry?
let isDoorLocked = true;         // Door is locked
let isRaining = false;           // It's not raining
let hasDriverLicense = true;     // You have a license

// 4. UNDEFINED - Like an empty form field you haven't filled yet
// Real-life: A question you haven't answered yet
let phoneNumber;                 // You haven't provided your number yet
console.log(phoneNumber);        // undefined

// 5. NULL - Like intentionally leaving something blank
// Real-life: "Middle name: None" on a form
let middleName = null;           // Intentionally no middle name

// 6. OBJECT - Like a contact card with multiple details
// Real-life: A person's profile, a product listing
let student = {
  name: "Alice",
  age: 20,
  grade: "A",
  isEnrolled: true
};

// 7. ARRAY - Like a shopping list or playlist
// Real-life: Grocery list, to-do list, song playlist
let shoppingList = ["milk", "eggs", "bread", "butter"];
let todoList = ["Wake up", "Exercise", "Study", "Sleep"];

// Check data type - Like asking "What kind of information is this?"
console.log(typeof customerName);  // "string" - It's text
console.log(typeof productPrice);  // "number" - It's a number
console.log(typeof isDoorLocked);  // "boolean" - It's yes/no
```

---

## Operators

### Arithmetic Operators

**Real-Life Scenario:** Like using a calculator at a store or splitting a restaurant bill:

```javascript
// Shopping at a store
let itemPrice = 10;
let quantity = 3;

// Addition - Total cost of items
let totalCost = itemPrice + quantity;  // $13 (if you buy 3 items at $10 each... wait, that's wrong!)
let correctTotal = itemPrice * quantity; // $30 (correct calculation)

// Real-life examples:
let groceryBill = 45;
let restaurantBill = 32;
let totalSpending = groceryBill + restaurantBill;  // $77 total spent today

// Subtraction - Money left after shopping
let walletMoney = 100;
let spent = 35;
let moneyLeft = walletMoney - spent;  // $65 remaining

// Multiplication - Buying multiple items
let pricePerPizza = 12;
let numberOfPizzas = 4;
let pizzaTotal = pricePerPizza * numberOfPizzas;  // $48 for 4 pizzas

// Division - Splitting a bill among friends
let restaurantTotal = 120;
let numberOfFriends = 4;
let perPersonCost = restaurantTotal / numberOfFriends;  // $30 per person

// Modulus (%) - Finding remainder (like leftover pizza slices)
let totalSlices = 10;
let peopleEating = 3;
let leftoverSlices = totalSlices % peopleEating;  // 1 slice left over
// (Each person gets 3 slices, 1 slice remains)

// Exponentiation (**) - Calculating compound interest or area
let sideLength = 5;
let squareArea = sideLength ** 2;  // 25 square meters

// Increment/Decrement - Like a visitor counter
let visitorCount = 100;
visitorCount++;  // 101 (one more visitor arrived)
visitorCount--;  // 100 (one visitor left)
```

### Comparison Operators

**Real-Life Scenario:** Like comparing prices, ages, or checking if you have the right password:

```javascript
// Shopping - Comparing prices
let storeAPrice = 50;
let storeBPrice = 45;

console.log(storeBPrice < storeAPrice);  // true - Store B is cheaper!

// Age verification - Checking if someone can vote
let personAge = 18;
let votingAge = 18;
console.log(personAge >= votingAge);  // true - Can vote!

// Password checking - Loose vs Strict comparison
let userInput = "1234";      // User typed this (it's text)
let correctPin = 1234;       // Stored as a number

// Loose equality (==) - Like saying "close enough"
// Converts types before comparing
console.log(userInput == correctPin);   // true - JavaScript converts "1234" to 1234

// Strict equality (===) - Like saying "must be exactly the same"
// Checks both value AND type
console.log(userInput === correctPin);  // false - One is text, one is number

// Real-world example: Height requirement for a ride
let childHeight = 120;  // cm
let minimumHeight = 110;
let canRide = childHeight >= minimumHeight;  // true - Tall enough!

// Checking if items are different
let selectedSize = "M";
let availableSize = "L";
console.log(selectedSize !== availableSize);  // true - Sizes don't match

// Temperature check
let currentTemp = 25;
let comfortableTemp = 22;
console.log(currentTemp > comfortableTemp);  // true - It's warmer than comfortable
```

### Logical Operators

**Real-Life Scenario:** Like making decisions based on multiple conditions:

```javascript
// Scenario 1: Can you drive a car?
// You need BOTH a license AND to be 18+
let hasDriverLicense = true;
let age = 20;
let canDriveLegally = hasDriverLicense && age >= 18;
console.log(canDriveLegally);  // true - Has license AND is old enough

// Scenario 2: Can you enter the club?
// You need EITHER a VIP pass OR to pay the entry fee
let hasVIPPass = false;
let paidEntryFee = true;
let canEnterClub = hasVIPPass || paidEntryFee;
console.log(canEnterClub);  // true - Paid the fee (OR condition satisfied)

// Scenario 3: Is the store closed?
let isWeekend = false;
let isHoliday = false;
let isStoreClosed = isWeekend || isHoliday;
console.log(isStoreClosed);  // false - Store is open (not weekend, not holiday)

// Scenario 4: Checking if someone is NOT a member
let isMember = false;
let needsToSignUp = !isMember;
console.log(needsToSignUp);  // true - Not a member, so needs to sign up

// Real-world: Online shopping eligibility
let hasAccount = true;
let hasPaymentMethod = true;
let itemInStock = true;
let canCheckout = hasAccount && hasPaymentMethod && itemInStock;
console.log(canCheckout);  // true - All conditions met!

// Real-world: Discount eligibility
// Get discount if you're a student OR a senior citizen
let isStudent = false;
let isSenior = true;
let getsDiscount = isStudent || isSenior;
console.log(getsDiscount);  // true - Senior gets discount

// Real-world: Access denied
let isLoggedIn = false;
let accessDenied = !isLoggedIn;
console.log(accessDenied);  // true - Not logged in, so access denied
```

---

## Control Flow

### If-Else Statements

**Real-Life Scenario:** Like making decisions based on situations - "If it's raining, take an umbrella, otherwise wear sunglasses"

```javascript
// Scenario 1: Movie ticket pricing
let age = 15;

if (age >= 18) {
  console.log("Adult ticket: $15");
} else if (age >= 13) {
  console.log("Teen ticket: $10");  // This runs!
} else {
  console.log("Child ticket: $8");
}

// Scenario 2: Weather-based clothing advice
let temperature = 10;  // Celsius

if (temperature < 0) {
  console.log("Wear a heavy winter coat!");
} else if (temperature < 15) {
  console.log("Wear a jacket");  // This runs!
} else if (temperature < 25) {
  console.log("Wear a light shirt");
} else {
  console.log("Wear shorts and t-shirt");
}

// Scenario 3: Coffee shop order
let accountBalance = 5;
let coffeePrice = 4;

if (accountBalance >= coffeePrice) {
  console.log("Order confirmed! Enjoy your coffee ☕");
  accountBalance = accountBalance - coffeePrice;
} else {
  console.log("Insufficient funds. Please add money to your account.");
}

// Ternary operator - Quick decision (like a shortcut)
// Real-life: Checking if a store is open
let currentHour = 14;  // 2 PM
let storeStatus = currentHour < 20 ? "Open" : "Closed";
console.log(storeStatus);  // "Open"

// Another example: Exam result
let examScore = 75;
let result = examScore >= 60 ? "Pass 🎉" : "Fail 😞";
console.log(result);  // "Pass 🎉"
```

### Switch Statement

**Real-Life Scenario:** Like a restaurant menu where you choose one option from many - "What would you like to order?"

```javascript
// Scenario 1: Traffic light system
let lightColor = "yellow";

switch (lightColor) {
  case "red":
    console.log("🛑 STOP! Don't cross the road.");
    break;
  case "yellow":
    console.log("⚠️ SLOW DOWN! Prepare to stop.");  // This runs!
    break;
  case "green":
    console.log("✅ GO! Safe to cross.");
    break;
  default:
    console.log("⚠️ Light malfunction! Be careful.");
}

// Scenario 2: Food delivery status
let orderStatus = "preparing";

switch (orderStatus) {
  case "received":
    console.log("📧 Order received! We're processing it.");
    break;
  case "preparing":
    console.log("🍳 Chef is preparing your food!");  // This runs!
    break;
  case "out-for-delivery":
    console.log("🚚 On the way! Driver is coming.");
    break;
  case "delivered":
    console.log("✅ Delivered! Enjoy your meal!");
    break;
  default:
    console.log("❓ Unknown status. Please contact support.");
}

// Scenario 3: Day of the week activities
let dayNumber = 6;  // Saturday

switch (dayNumber) {
  case 1:
    console.log("💼 Monday - Work day");
    break;
  case 2:
  case 3:
  case 4:
  case 5:
    console.log("💼 Weekday - Time to work/study");
    break;
  case 6:
  case 7:
    console.log("🎉 Weekend - Time to relax!");  // This runs!
    break;
  default:
    console.log("❌ Invalid day number");
}
```

### Loops

**Real-Life Scenario:** Loops are like repetitive tasks - doing the same thing multiple times

```javascript
// FOR LOOP - Like counting items in a box
// Scenario: Printing tickets for a concert
console.log("Printing concert tickets:");
for (let ticketNumber = 1; ticketNumber <= 5; ticketNumber++) {
  console.log(`Ticket #${ticketNumber}`);
}
// Output: Ticket #1, Ticket #2, Ticket #3, Ticket #4, Ticket #5

// Scenario: Climbing stairs
console.log("Climbing stairs:");
for (let step = 1; step <= 10; step++) {
  console.log(`Step ${step} - Keep going!`);
}
console.log("You reached the top!");

// WHILE LOOP - Like waiting for something to happen
// Scenario: Waiting for water to boil
let waterTemperature = 20;  // Starting at 20 degrees
console.log("Heating water...");

while (waterTemperature < 100) {
  waterTemperature += 10;  // Temperature increases by 10 degrees
  console.log(`Temperature: ${waterTemperature} degrees`);
}
console.log("Water is boiling! Time to make tea.");

// Scenario: Saving money until you reach a goal
let savings = 0;
let savingsGoal = 100;
let week = 0;

while (savings < savingsGoal) {
  week++;
  savings += 20;  // Save $20 per week
  console.log(`Week ${week}: Saved $${savings}`);
}
console.log(`Goal reached! You saved $${savings}!`);

// DO-WHILE LOOP - Like trying at least once
// Scenario: ATM PIN entry (try at least once)
let enteredPIN = 0000;
let correctPIN = 1234;
let attempts = 0;

do {
  attempts++;
  console.log(`Attempt ${attempts}: Checking PIN...`);
  if (enteredPIN === correctPIN) {
    console.log("Access granted!");
  } else {
    console.log("Wrong PIN. Try again.");
    enteredPIN = 1234;  // User tries correct PIN
  }
} while (enteredPIN !== correctPIN && attempts < 3);

// FOR...OF LOOP - Like going through a shopping list
// Scenario: Checking items in your grocery bag
let groceryBag = ["apples", "bread", "milk", "eggs"];

console.log("Items in your grocery bag:");
for (let item of groceryBag) {
  console.log(`Item: ${item}`);
}

// Scenario: Reading notifications
let notifications = [
  "New message from John",
  "Your order has shipped",
  "Reminder: Meeting at 3 PM"
];

console.log("Your notifications:");
for (let notification of notifications) {
  console.log(notification);
}

// FOR...IN LOOP - Like reading a contact card
// Scenario: Displaying user profile information
let userProfile = {
  name: "Sarah",
  age: 28,
  city: "New York",
  occupation: "Designer"
};

console.log("User Profile:");
for (let field in userProfile) {
  console.log(`${field}: ${userProfile[field]}`);
}
// Output:
// name: Sarah
// age: 28
// city: New York
// occupation: Designer
```

---

## Functions

**Real-Life Scenario:** Functions are like recipes or instruction manuals - you write the steps once, then use them whenever needed.

### Function Declaration

```javascript
// Scenario 1: Greeting customers at a store
// Instead of saying "Hello" to each customer manually,
// create a function that does it automatically
function greetCustomer(customerName) {
  return "Welcome to our store, " + customerName + "! How can we help you today?";
}

// Now use it for different customers
console.log(greetCustomer("Alice"));   // "Welcome to our store, Alice! How can we help you today?"
console.log(greetCustomer("Bob"));     // "Welcome to our store, Bob! How can we help you today?"
console.log(greetCustomer("Charlie")); // "Welcome to our store, Charlie! How can we help you today?"

// Scenario 2: Calculating pizza cost with default tip
// Like a calculator that remembers the formula
function calculatePizzaCost(pizzaPrice, numberOfPizzas = 1) {
  let total = pizzaPrice * numberOfPizzas;
  return total;
}

console.log(calculatePizzaCost(12, 3));  // $36 (3 pizzas at $12 each)
console.log(calculatePizzaCost(15));     // $15 (1 pizza, using default)

// Scenario 3: Temperature converter
// Like having a conversion chart you can use anytime
function celsiusToFahrenheit(celsius) {
  let fahrenheit = (celsius * 9/5) + 32;
  return fahrenheit;
}

console.log(celsiusToFahrenheit(0));   // 32°F (freezing point)
console.log(celsiusToFahrenheit(100)); // 212°F (boiling point)
console.log(celsiusToFahrenheit(25));  // 77°F (room temperature)
```

### Function Expression

**Real-Life Scenario:** Like storing a recipe in a cookbook - you save the instructions with a name

```javascript
// Scenario: Restaurant bill calculator
// Store the calculation method in a variable
const calculateBill = function(mealCost, tipPercent) {
  let tip = mealCost * (tipPercent / 100);
  let total = mealCost + tip;
  return total;
};

console.log(calculateBill(50, 15));  // $57.50 (meal + 15% tip)
console.log(calculateBill(100, 20)); // $120 (meal + 20% tip)
```

### Arrow Functions (ES6)

**Real-Life Scenario:** Arrow functions are like shortcuts - a faster way to write functions

```javascript
// Scenario 1: Quick discount calculator
// Old way (longer)
const oldDiscount = function(price) {
  return price * 0.9;  // 10% off
};

// New way (shorter and cleaner)
const quickDiscount = (price) => price * 0.9;

console.log(quickDiscount(100));  // $90 (10% off)

// Scenario 2: Area calculator
const calculateRectangleArea = (length, width) => length * width;

console.log(calculateRectangleArea(5, 10));  // 50 square meters

// Scenario 3: Full name generator (multiple lines)
const createFullName = (firstName, lastName) => {
  let fullName = firstName + " " + lastName;
  let greeting = `Hello, ${fullName}!`;
  return greeting;
};

console.log(createFullName("John", "Doe"));  // "Hello, John Doe!"
```

### Callback Functions

**Real-Life Scenario:** Like giving someone instructions to do AFTER they finish a task

```javascript
// Scenario: Food delivery system
// First prepare the food, THEN notify the customer
function prepareOrder(dishName, notifyCustomer) {
  console.log(`Chef is preparing: ${dishName}`);
  console.log("Cooking... (3 minutes)");
  
  // After cooking is done, call the notification function
  notifyCustomer();
}

// Use it
prepareOrder("Pasta", function() {
  console.log("Your order is ready! Please pick it up.");
});

// Output:
// Chef is preparing: Pasta
// Cooking... (3 minutes)
// Your order is ready! Please pick it up.

// Scenario 2: Washing machine
function washClothes(clothesType, whenDone) {
  console.log(`Washing ${clothesType}...`);
  whenDone();
}

washClothes("shirts", function() {
  console.log("Beep beep! Washing complete. Please remove clothes.");
});
```

---

## Arrays

**Real-Life Scenario:** Arrays are like lists - shopping lists, to-do lists, playlists, contact lists

### Creating and Accessing Arrays

```javascript
// Scenario: Your weekly meal plan
let mealPlan = ["Pizza", "Salad", "Pasta", "Burger", "Sushi"];

// Access specific days
console.log(mealPlan[0]);     // "Pizza" - Monday's meal (first item)
console.log(mealPlan[2]);     // "Pasta" - Wednesday's meal (third item)
console.log(mealPlan[4]);     // "Sushi" - Friday's meal (fifth item)

// How many meals planned?
console.log(mealPlan.length); // 5 meals

// Change a meal plan
mealPlan[1] = "Tacos";  // Changed Tuesday from Salad to Tacos
console.log(mealPlan);  // ["Pizza", "Tacos", "Pasta", "Burger", "Sushi"]
```

### Array Methods

**Real-Life Scenario:** Array methods are like different ways to organize and manage your lists

```javascript
// Starting with a playlist
let playlist = ["Song A", "Song B", "Song C"];

// PUSH - Add song to end of playlist (like adding to bottom of list)
playlist.push("Song D");
console.log(playlist);  // ["Song A", "Song B", "Song C", "Song D"]

// POP - Remove last song (like removing bottom item)
let removed = playlist.pop();
console.log(removed);   // "Song D" (the removed song)
console.log(playlist);  // ["Song A", "Song B", "Song C"]

// UNSHIFT - Add song to beginning (like adding to top of list)
playlist.unshift("Song Z");
console.log(playlist);  // ["Song Z", "Song A", "Song B", "Song C"]

// SHIFT - Remove first song (like removing top item)
let firstSong = playlist.shift();
console.log(firstSong); // "Song Z"
console.log(playlist);  // ["Song A", "Song B", "Song C"]

// Scenario: Shopping cart
let cart = ["Laptop", "Mouse", "Keyboard"];

// INDEXOF - Find position of item (like finding item in a list)
let position = cart.indexOf("Mouse");
console.log(position);  // 1 (Mouse is at position 1)

// INCLUDES - Check if item exists (like checking if you have something)
let hasKeyboard = cart.includes("Keyboard");
console.log(hasKeyboard);  // true

let hasMonitor = cart.includes("Monitor");
console.log(hasMonitor);   // false

// MAP - Transform each item (like applying discount to all prices)
let prices = [100, 50, 75, 200];
let discountedPrices = prices.map(price => price * 0.8);  // 20% off
console.log(discountedPrices);  // [80, 40, 60, 160]

// Real example: Converting temperatures
let celsiusTemps = [0, 10, 20, 30];
let fahrenheitTemps = celsiusTemps.map(temp => (temp * 9/5) + 32);
console.log(fahrenheitTemps);  // [32, 50, 68, 86]

// FILTER - Keep only items that match condition (like filtering search results)
let ages = [12, 18, 25, 16, 30, 14];
let adults = ages.filter(age => age >= 18);
console.log(adults);  // [18, 25, 30] - only adults

// Real example: Finding available products
let products = [
  { name: "Laptop", inStock: true },
  { name: "Phone", inStock: false },
  { name: "Tablet", inStock: true }
];
let availableProducts = products.filter(product => product.inStock);
console.log(availableProducts);  // Only Laptop and Tablet

// REDUCE - Combine all items into one value (like calculating total)
let orderPrices = [25, 50, 15, 30];
let totalCost = orderPrices.reduce((total, price) => total + price, 0);
console.log(totalCost);  // 120 (sum of all prices)

// Real example: Counting total items in cart
let cartItems = [
  { name: "Apple", quantity: 3 },
  { name: "Banana", quantity: 5 },
  { name: "Orange", quantity: 2 }
];
let totalItems = cartItems.reduce((sum, item) => sum + item.quantity, 0);
console.log(totalItems);  // 10 total items

// FOREACH - Do something with each item (like checking off to-do list)
let tasks = ["Wake up", "Exercise", "Breakfast", "Work"];
tasks.forEach(task => {
  console.log(`Completed: ${task}`);
});

// SORT - Arrange in order (like organizing alphabetically)
let names = ["Charlie", "Alice", "Bob"];
names.sort();
console.log(names);  // ["Alice", "Bob", "Charlie"]

// REVERSE - Flip the order (like reading list backwards)
let numbers = [1, 2, 3, 4, 5];
numbers.reverse();
console.log(numbers);  // [5, 4, 3, 2, 1]

// SLICE - Copy a portion (like taking a few items from list)
let weekDays = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"];
let workDays = weekDays.slice(0, 5);  // First 5 days
console.log(workDays);  // ["Mon", "Tue", "Wed", "Thu", "Fri"]

// SPLICE - Remove and/or add items (like editing a list)
let menu = ["Burger", "Pizza", "Salad", "Pasta"];
menu.splice(2, 1, "Tacos");  // Remove 1 item at position 2, add "Tacos"
console.log(menu);  // ["Burger", "Pizza", "Tacos", "Pasta"]
```

---

## Objects

**Real-Life Scenario:** Objects are like ID cards or profiles - they store multiple related pieces of information about one thing

### Creating Objects

```javascript
// Scenario: Student ID Card
let studentCard = {
  firstName: "Emma",
  lastName: "Wilson",
  studentID: "STU12345",
  age: 20,
  major: "Computer Science",
  isEnrolled: true,
  
  // Method - like an action the student can do
  introduce: function() {
    return `Hi, I'm ${this.firstName} ${this.lastName}, studying ${this.major}`;
  }
};

// Accessing information (two ways)
// Dot notation - like reading fields on an ID card
console.log(studentCard.firstName);      // "Emma"
console.log(studentCard.major);          // "Computer Science"

// Bracket notation - useful when field name is in a variable
console.log(studentCard["studentID"]);   // "STU12345"
let field = "age";
console.log(studentCard[field]);         // 20

// Calling methods - like asking the student to introduce themselves
console.log(studentCard.introduce());    // "Hi, I'm Emma Wilson, studying Computer Science"

// Adding new information - like updating your profile
studentCard.email = "emma.wilson@university.edu";
studentCard.phoneNumber = "555-0123";

// Removing information - like deleting old data
delete studentCard.phoneNumber;

// Scenario 2: Product in an online store
let product = {
  name: "Wireless Headphones",
  brand: "SoundMax",
  price: 79.99,
  inStock: true,
  colors: ["Black", "White", "Blue"],
  rating: 4.5,
  
  applyDiscount: function(percent) {
    this.price = this.price * (1 - percent / 100);
    return `New price: $${this.price.toFixed(2)}`;
  }
};

console.log(product.name);              // "Wireless Headphones"
console.log(product.applyDiscount(20)); // "New price: $63.99" (20% off)
```

### Object Methods

**Real-Life Scenario:** Object methods help you work with objects - like tools to analyze and organize information

```javascript
// Scenario: Restaurant menu item
let menuItem = {
  name: "Margherita Pizza",
  price: 12.99,
  category: "Main Course",
  isVegetarian: true
};

// Object.keys() - Get all field names (like getting column headers)
let fields = Object.keys(menuItem);
console.log(fields);  // ["name", "price", "category", "isVegetarian"]
// Use case: You want to know what information is stored

// Object.values() - Get all values (like getting all the data)
let values = Object.values(menuItem);
console.log(values);  // ["Margherita Pizza", 12.99, "Main Course", true]
// Use case: You want to see all the actual information

// Object.entries() - Get pairs of field names and values
let entries = Object.entries(menuItem);
console.log(entries);
// [["name", "Margherita Pizza"], ["price", 12.99], ["category", "Main Course"], ["isVegetarian", true]]
// Use case: You want both the labels and the data together

// Real example: Displaying product details
for (let [key, value] of Object.entries(menuItem)) {
  console.log(`${key}: ${value}`);
}
// Output:
// name: Margherita Pizza
// price: 12.99
// category: Main Course
// isVegetarian: true

// Object.assign() - Copy object (like making a photocopy)
let originalRecipe = { ingredient1: "flour", ingredient2: "water" };
let recipeCopy = Object.assign({}, originalRecipe);
console.log(recipeCopy);  // { ingredient1: "flour", ingredient2: "water" }

// Spread operator - Modern way to copy (like using a copy machine)
let person = { name: "John", age: 30 };
let personWithCity = { ...person, city: "New York" };
console.log(personWithCity);  // { name: "John", age: 30, city: "New York" }
// Use case: Adding new information while keeping the old
```

### Destructuring

**Real-Life Scenario:** Destructuring is like unpacking a suitcase - taking specific items out and giving them names

```javascript
// Scenario 1: Unpacking a delivery package
let package = {
  recipientName: "Sarah",
  address: "123 Main St",
  item: "Laptop",
  price: 999
};

// Old way - taking items out one by one
let recipientName = package.recipientName;
let item = package.item;

// New way - destructuring (unpack multiple items at once)
let { recipientName, address, item, price } = package;

console.log(recipientName);  // "Sarah"
console.log(item);           // "Laptop"
console.log(price);          // 999

// Use case: You only need specific information from a large object

// Scenario 2: Getting specific items from a shopping order
let order = {
  orderID: "ORD123",
  customerName: "Mike",
  total: 150,
  status: "shipped",
  trackingNumber: "TRACK456"
};

// Only extract what you need
let { customerName, status } = order;
console.log(`${customerName}'s order is ${status}`);  // "Mike's order is shipped"

// Array destructuring - like taking specific items from a list
let topScores = [98, 95, 92, 88, 85];

// Get first three scores
let [first, second, third] = topScores;
console.log(first);   // 98
console.log(second);  // 95
console.log(third);   // 92

// Real example: Getting coordinates
let location = [40.7128, -74.0060];  // [latitude, longitude]
let [latitude, longitude] = location;
console.log(`Lat: ${latitude}, Long: ${longitude}`);
// Output: "Lat: 40.7128, Long: -74.0060"
```

---

## DOM Manipulation

**Real-Life Scenario:** DOM Manipulation is like rearranging furniture in your house or updating a bulletin board - you're changing what people see on the webpage

### Selecting Elements

**Real-Life Scenario:** Like finding a specific book in a library or a specific person in a crowd

```javascript
// Scenario: Finding elements on a webpage (like finding items in a store)

// getElementById - Like finding someone by their ID card number (unique)
let header = document.getElementById("header");
// Use case: Finding the main header of your page

// querySelector - Like finding the first red car in a parking lot
let firstButton = document.querySelector(".btn");
// Use case: Finding the first button with class "btn"

// querySelectorAll - Like finding ALL red cars in the parking lot
let allButtons = document.querySelectorAll(".btn");
// Use case: Finding all buttons to change them at once

// getElementsByTagName - Like finding all books (not magazines) in a library
let allParagraphs = document.getElementsByTagName("p");
// Use case: Finding all paragraph elements
```

### Modifying Elements

**Real-Life Scenario:** Like editing a poster, changing a sign, or repainting a wall

```javascript
// Scenario 1: Updating a welcome message (like changing a store sign)
let welcomeMessage = document.getElementById("welcome");
welcomeMessage.textContent = "Welcome back, Sarah!";
// Use case: Personalizing the greeting when user logs in

// Scenario 2: Changing product information (like updating a price tag)
let productPrice = document.getElementById("price");
productPrice.innerHTML = "<strong>$29.99</strong> <span class='sale'>On Sale!</span>";
// Use case: Showing sale price with special formatting

// Scenario 3: Updating an image (like changing a billboard)
let productImage = document.querySelector("img");
productImage.src = "new-product.jpg";
productImage.alt = "New Product Image";
// Use case: Showing different product when user selects a color

// Scenario 4: Changing styles (like redecorating a room)
let notification = document.getElementById("notification");
notification.style.backgroundColor = "green";  // Change background color
notification.style.color = "white";            // Change text color
notification.style.padding = "15px";           // Add padding
notification.style.borderRadius = "5px";       // Round corners
// Use case: Making a success notification stand out

// Scenario 5: Adding/removing CSS classes (like changing outfits)
let menuButton = document.getElementById("menu-btn");
menuButton.classList.add("active");      // Add "active" class (like putting on a jacket)
menuButton.classList.remove("hidden");   // Remove "hidden" class (like taking off a hat)
menuButton.classList.toggle("open");     // Toggle "open" class (like switching a light on/off)

if (menuButton.classList.contains("active")) {
  console.log("Menu is active!");
}
// Use case: Showing/hiding mobile menu when button is clicked
```

### Creating and Removing Elements

**Real-Life Scenario:** Like adding a new item to a shelf or removing an old poster from a wall

```javascript
// Scenario 1: Adding a new item to a shopping cart
let cartList = document.getElementById("cart-items");

// Create new list item (like adding a product to cart)
let newItem = document.createElement("li");
newItem.textContent = "Wireless Mouse - $25";
newItem.className = "cart-item";

// Add it to the cart
cartList.appendChild(newItem);
// Use case: When user clicks "Add to Cart", show the item in cart

// Scenario 2: Creating a notification message
let notificationArea = document.getElementById("notifications");

let notification = document.createElement("div");
notification.className = "alert alert-success";
notification.innerHTML = "<strong>Success!</strong> Your order has been placed.";

notificationArea.appendChild(notification);
// Use case: Showing success message after form submission

// Scenario 3: Removing an item (like deleting a completed task)
let completedTask = document.getElementById("task-5");
completedTask.remove();
// Use case: Removing a to-do item when user marks it as complete

// Scenario 4: Removing all items (like clearing a shopping cart)
let cart = document.getElementById("cart");
cart.innerHTML = "";  // Clears everything inside
// Use case: "Clear Cart" button removes all items
```

---

## Events

**Real-Life Scenario:** Events are like reactions to things that happen - when someone knocks on your door (event), you open it (response)

### Adding Event Listeners

**Real-Life Scenario:** Setting up automatic responses to user actions

```javascript
// Scenario 1: Like Button (like pressing a doorbell)
let likeButton = document.getElementById("likeBtn");
let likeCount = 0;

likeButton.addEventListener("click", function() {
  likeCount++;
  console.log(`Post liked! Total likes: ${likeCount}`);
  likeButton.textContent = `❤️ ${likeCount} Likes`;
});
// Use case: Instagram/Facebook like button

// Scenario 2: Search box (like typing in a search bar)
let searchInput = document.getElementById("search");
let searchResults = document.getElementById("results");

searchInput.addEventListener("input", function(e) {
  let searchTerm = e.target.value;
  console.log(`Searching for: ${searchTerm}`);
  // Show search results as user types
  searchResults.textContent = `Searching for "${searchTerm}"...`;
});
// Use case: Google search suggestions as you type

// Scenario 3: Form submission (like submitting an application)
let contactForm = document.getElementById("contactForm");

contactForm.addEventListener("submit", function(e) {
  e.preventDefault(); // Stop page from reloading (like catching a ball before it hits the ground)
  
  let name = document.getElementById("name").value;
  let email = document.getElementById("email").value;
  
  console.log(`Form submitted by ${name} (${email})`);
  alert("Thank you! We'll contact you soon.");
});
// Use case: Contact form, registration form

// Scenario 4: Hover effect (like a motion sensor light)
let productCard = document.getElementById("product");

productCard.addEventListener("mouseenter", function() {
  this.style.transform = "scale(1.05)";  // Make it slightly bigger
  this.style.boxShadow = "0 5px 15px rgba(0,0,0,0.3)";
  console.log("User is looking at this product!");
});

productCard.addEventListener("mouseleave", function() {
  this.style.transform = "scale(1)";  // Back to normal size
  this.style.boxShadow = "none";
});
// Use case: Product cards that highlight when you hover over them
```

### Common Events

**Real-Life Scenario:** Different types of interactions users can have with your website

```javascript
// MOUSE EVENTS - Like different ways to interact with a touchscreen

let button = document.getElementById("actionBtn");

// Click - Like tapping once
button.addEventListener("click", () => {
  console.log("Button clicked once!");
});

// Double click - Like tapping twice quickly
button.addEventListener("dblclick", () => {
  console.log("Button double-clicked!");
});

// Mouse enter - Like hovering your hand over a sensor
button.addEventListener("mouseenter", () => {
  console.log("Mouse entered button area");
});

// Mouse leave - Like moving your hand away from a sensor
button.addEventListener("mouseleave", () => {
  console.log("Mouse left button area");
});

// KEYBOARD EVENTS - Like typing on a keyboard

let textInput = document.getElementById("message");

// Key down - When key is pressed (like pressing a piano key)
textInput.addEventListener("keydown", (e) => {
  console.log(`Key pressed: ${e.key}`);
  
  // Special keys
  if (e.key === "Enter") {
    console.log("Enter key pressed - submit form!");
  }
  if (e.key === "Escape") {
    console.log("Escape pressed - close modal!");
  }
});

// Key up - When key is released
textInput.addEventListener("keyup", (e) => {
  console.log(`Key released: ${e.key}`);
});

// FORM EVENTS - Like filling out a paper form

let emailInput = document.getElementById("email");

// Focus - When user clicks into input field (like picking up a pen)
emailInput.addEventListener("focus", () => {
  emailInput.style.borderColor = "blue";
  console.log("User is now typing in email field");
});

// Blur - When user clicks away from input field (like putting down a pen)
emailInput.addEventListener("blur", () => {
  emailInput.style.borderColor = "gray";
  console.log("User left email field");
  
  // Validate email when user leaves the field
  if (!emailInput.value.includes("@")) {
    alert("Please enter a valid email!");
  }
});

// Change - When value changes (like checking a checkbox)
let agreeCheckbox = document.getElementById("agree");
agreeCheckbox.addEventListener("change", (e) => {
  if (e.target.checked) {
    console.log("User agreed to terms");
  } else {
    console.log("User disagreed");
  }
});

// Real-world example: Character counter for textarea
let messageBox = document.getElementById("message");
let charCount = document.getElementById("charCount");

messageBox.addEventListener("input", (e) => {
  let remaining = 280 - e.target.value.length;  // Like Twitter's character limit
  charCount.textContent = `${remaining} characters remaining`;
  
  if (remaining < 0) {
    charCount.style.color = "red";
  } else {
    charCount.style.color = "black";
  }
});
```

---

## Asynchronous JavaScript

**Real-Life Scenario:** Asynchronous code is like ordering food for delivery - you place the order (start the task), do other things while waiting (continue with other code), and handle the food when it arrives (process the result)

### setTimeout and setInterval

**Real-Life Scenario:** Setting timers and alarms

```javascript
// setTimeout - Like setting a kitchen timer (runs once)
// Scenario 1: Auto-hide notification after 3 seconds
console.log("Notification: File uploaded successfully!");

setTimeout(function() {
  console.log("Notification hidden");
  // Hide the notification element
  document.getElementById("notification").style.display = "none";
}, 3000);  // 3000 milliseconds = 3 seconds

// Use case: Toast notifications that disappear automatically

// Scenario 2: Delayed redirect (like "Redirecting in 5 seconds...")
console.log("Thank you for your purchase!");
console.log("Redirecting to homepage in 5 seconds...");

setTimeout(function() {
  window.location.href = "/homepage";
}, 5000);

// setInterval - Like a recurring alarm (runs repeatedly)
// Scenario 3: Live clock (updates every second)
let clockElement = document.getElementById("clock");

setInterval(function() {
  let now = new Date();
  let timeString = now.toLocaleTimeString();
  clockElement.textContent = timeString;
  console.log("Current time: " + timeString);
}, 1000);  // Update every 1 second

// Use case: Digital clock, countdown timer, auto-refresh data

// Scenario 4: Countdown timer (like a bomb timer in movies)
let timeLeft = 10;
let countdownElement = document.getElementById("countdown");

let countdownInterval = setInterval(function() {
  timeLeft--;
  countdownElement.textContent = `Time left: ${timeLeft} seconds`;
  console.log(`${timeLeft} seconds remaining`);
  
  if (timeLeft <= 0) {
    clearInterval(countdownInterval);  // Stop the timer
    console.log("Time's up!");
    alert("Sale has ended!");
  }
}, 1000);

// Use case: Flash sale countdown, exam timer, OTP expiry timer

// Scenario 5: Auto-save feature (like Google Docs)
let documentContent = "";

setInterval(function() {
  // Save document every 30 seconds
  console.log("Auto-saving document...");
  // Save to server or local storage
  localStorage.setItem("draft", documentContent);
  console.log("Document saved!");
}, 30000);  // Every 30 seconds
```

### Promises

**Real-Life Scenario:** Promises are like ordering food online - you get a promise that food will arrive, it's either fulfilled (delivered) or rejected (cancelled)

```javascript
// Scenario 1: Checking if user is old enough
function checkAge(age) {
  return new Promise((resolve, reject) => {
    console.log("Checking age...");
    
    setTimeout(() => {  // Simulating a delay (like checking a database)
      if (age >= 18) {
        resolve("Access granted! You are old enough.");
      } else {
        reject("Access denied! You must be 18 or older.");
      }
    }, 2000);  // 2 second delay
  });
}

// Using the promise
checkAge(20)
  .then(message => {
    console.log(message);  // "Access granted! You are old enough."
    // Show adult content
  })
  .catch(error => {
    console.log(error);  // "Access denied! You must be 18 or older."
    // Show error message
  });

// Scenario 2: Fetching user data from server
function getUserData(userId) {
  return new Promise((resolve, reject) => {
    console.log(`Fetching data for user ${userId}...`);
    
    // Simulating API call
    setTimeout(() => {
      let success = true;  // Imagine this depends on server response
      
      if (success) {
        let userData = {
          id: userId,
          name: "John Doe",
          email: "john@example.com"
        };
        resolve(userData);
      } else {
        reject("Failed to fetch user data. Server error.");
      }
    }, 1500);
  });
}

getUserData(123)
  .then(user => {
    console.log("User data received:", user);
    // Display user profile
  })
  .catch(error => {
    console.log("Error:", error);
    // Show error message to user
  })
  .finally(() => {
    console.log("Request completed");  // Runs whether success or failure
    // Hide loading spinner
  });

// Use case: Loading user profile, fetching products, checking login status
```

### Async/Await

**Real-Life Scenario:** Async/await makes asynchronous code look like regular code - like writing a recipe step by step

```javascript
// Scenario 1: Ordering food delivery (step by step)
async function orderFood() {
  try {
    console.log("1. Opening food delivery app...");
    
    // Wait for restaurant list to load
    console.log("2. Loading restaurants...");
    await new Promise(resolve => setTimeout(resolve, 1000));  // Simulate 1 sec delay
    console.log("   Restaurants loaded!");
    
    // Wait for menu to load
    console.log("3. Loading menu...");
    await new Promise(resolve => setTimeout(resolve, 1000));
    console.log("   Menu loaded!");
    
    // Place order
    console.log("4. Placing order...");
    await new Promise(resolve => setTimeout(resolve, 1000));
    console.log("   Order placed!");
    
    // Wait for delivery
    console.log("5. Waiting for delivery...");
    await new Promise(resolve => setTimeout(resolve, 3000));
    console.log("   Food delivered! Enjoy your meal! 🍕");
    
  } catch (error) {
    console.log("Error:", error);
    console.log("Order failed. Please try again.");
  }
}

orderFood();
// Use case: Multi-step processes like checkout, registration, file upload

// Scenario 2: Fetching data from API (like getting weather information)
async function getWeather(city) {
  try {
    console.log(`Getting weather for ${city}...`);
    
    // Fetch weather data (simulated)
    let response = await fetch(`https://api.weather.com/data?city=${city}`);
    let data = await response.json();
    
    console.log(`Temperature in ${city}: ${data.temperature}°C`);
    console.log(`Condition: ${data.condition}`);
    
    return data;
    
  } catch (error) {
    console.log("Failed to get weather data:", error);
    console.log("Please check your internet connection.");
  }
}

getWeather("New York");
// Use case: Weather apps, stock prices, news feeds

// Scenario 3: User login process
async function loginUser(email, password) {
  try {
    console.log("Logging in...");
    
    // Step 1: Verify credentials
    let authResponse = await fetch("/api/login", {
      method: "POST",
      body: JSON.stringify({ email, password })
    });
    
    if (!authResponse.ok) {
      throw new Error("Invalid credentials");
    }
    
    let authData = await authResponse.json();
    console.log("Authentication successful!");
    
    // Step 2: Get user profile
    let profileResponse = await fetch(`/api/user/${authData.userId}`);
    let userProfile = await profileResponse.json();
    console.log("Profile loaded:", userProfile);
    
    // Step 3: Load user preferences
    let prefsResponse = await fetch(`/api/preferences/${authData.userId}`);
    let preferences = await prefsResponse.json();
    console.log("Preferences loaded:", preferences);
    
    console.log("Login complete! Welcome back!");
    return { user: userProfile, preferences };
    
  } catch (error) {
    console.log("Login failed:", error.message);
    alert("Login failed. Please check your credentials.");
  }
}

loginUser("user@example.com", "password123");
// Use case: Login systems, multi-step forms, data synchronization
```

---

## ES6+ Features

**Real-Life Scenario:** ES6+ features are like modern tools that make your work easier and faster

### Template Literals

**Real-Life Scenario:** Like filling in blanks in a form letter - easier than gluing pieces of paper together

```javascript
// Scenario: Creating personalized email messages
let customerName = "Alice";
let orderNumber = "ORD-12345";
let totalAmount = 99.99;

// Old way - Like cutting and pasting pieces of paper (messy!)
let oldMessage = "Dear " + customerName + ", your order " + orderNumber + " totaling $" + totalAmount + " has been confirmed.";

// New way - Template literals (clean and easy to read!)
let newMessage = `Dear ${customerName}, your order ${orderNumber} totaling $${totalAmount} has been confirmed.`;

console.log(newMessage);
// "Dear Alice, your order ORD-12345 totaling $99.99 has been confirmed."

// Use case: Email templates, SMS messages, dynamic content

// Multi-line strings (like writing a letter)
let emailBody = `
Hello ${customerName},

Thank you for your order!

Order Details:
- Order Number: ${orderNumber}
- Total: $${totalAmount}
- Estimated Delivery: 3-5 business days

Best regards,
The Team
`;

console.log(emailBody);
// Use case: Email templates, HTML generation, formatted text
```

### Spread Operator

**Real-Life Scenario:** Like unpacking a suitcase or combining multiple boxes into one

```javascript
// Scenario 1: Combining shopping lists
let groceryList1 = ["milk", "eggs", "bread"];
let groceryList2 = ["apples", "bananas", "oranges"];

// Old way - Like manually writing everything again
let combinedOld = groceryList1.concat(groceryList2);

// New way - Spread operator (like dumping both lists into one basket)
let combinedNew = [...groceryList1, ...groceryList2];
console.log(combinedNew);
// ["milk", "eggs", "bread", "apples", "bananas", "oranges"]

// Use case: Merging arrays, combining data

// Scenario 2: Adding items to a list
let myFavorites = ["pizza", "pasta"];
let allFoods = ["burger", ...myFavorites, "tacos"];
console.log(allFoods);
// ["burger", "pizza", "pasta", "tacos"]

// Scenario 3: Copying and updating user profile
let userProfile = {
  name: "John",
  age: 30,
  city: "New York"
};

// Create a copy and add new information (like photocopying and adding notes)
let updatedProfile = {
  ...userProfile,
  email: "john@example.com",
  phone: "555-0123"
};

console.log(updatedProfile);
// { name: "John", age: 30, city: "New York", email: "john@example.com", phone: "555-0123" }

// Use case: Updating user settings, creating variations of objects

// Scenario 4: Finding maximum value (like finding the tallest person)
let heights = [165, 180, 175, 190, 170];
let tallest = Math.max(...heights);  // Spread array into individual values
console.log(`Tallest person: ${tallest}cm`);
// Use case: Finding min/max values, statistical calculations
```

### Rest Parameters

**Real-Life Scenario:** Like a bag that collects all remaining items

```javascript
// Scenario 1: Restaurant bill calculator (any number of items)
function calculateTotal(...prices) {
  console.log(`Calculating total for ${prices.length} items...`);
  let total = prices.reduce((sum, price) => sum + price, 0);
  return total;
}

console.log(calculateTotal(10, 15, 20));           // $45 (3 items)
console.log(calculateTotal(5, 10, 15, 20, 25));    // $75 (5 items)
console.log(calculateTotal(100));                  // $100 (1 item)

// Use case: Functions that accept variable number of arguments

// Scenario 2: Group chat (first person is admin, rest are members)
function createGroupChat(admin, ...members) {
  console.log(`Admin: ${admin}`);
  console.log(`Members: ${members.join(", ")}`);
  console.log(`Total people: ${members.length + 1}`);
}

createGroupChat("Alice", "Bob", "Charlie", "David");
// Admin: Alice
// Members: Bob, Charlie, David
// Total people: 4

// Use case: Chat groups, team management, flexible functions
```

### Destructuring

**Real-Life Scenario:** Already covered in Objects section above - like unpacking specific items from a package

### Modules

**Real-Life Scenario:** Like organizing tools in different toolboxes and taking out only what you need

```javascript
// File: mathUtils.js (like a toolbox for math tools)
export function add(a, b) {
  return a + b;
}

export function subtract(a, b) {
  return a - b;
}

export function multiply(a, b) {
  return a * b;
}

export const PI = 3.14159;

// Default export (the main tool in this toolbox)
export default function divide(a, b) {
  return a / b;
}

// File: app.js (using the tools)
import divide, { add, subtract, PI } from './mathUtils.js';

console.log(add(5, 3));        // 8
console.log(subtract(10, 4));  // 6
console.log(divide(20, 4));    // 5
console.log(PI);               // 3.14159

// Use case: Organizing code, reusing functions, team collaboration

// Real-world example: E-commerce modules
// File: cart.js
export function addToCart(item) {
  console.log(`Added ${item} to cart`);
}

export function removeFromCart(item) {
  console.log(`Removed ${item} from cart`);
}

// File: payment.js
export function processPayment(amount) {
  console.log(`Processing payment of $${amount}`);
}

// File: main.js
import { addToCart, removeFromCart } from './cart.js';
import { processPayment } from './payment.js';

addToCart("Laptop");
processPayment(999);
```

---

## Best Practices

### 1. Use const and let, avoid var

```javascript
// ❌ Avoid
var x = 10;

// ✅ Use
const PI = 3.14159; // For values that don't change
let count = 0;      // For values that change
```

### 2. Use === instead of ==

```javascript
// ❌ Avoid (loose equality)
if (x == "5") { }

// ✅ Use (strict equality)
if (x === 5) { }
```

### 3. Use meaningful variable names

```javascript
// ❌ Avoid
let x = 25;
let y = "John";

// ✅ Use
let age = 25;
let userName = "John";
```

### 4. Keep functions small and focused

```javascript
// ❌ Avoid - function does too much
function processUser(user) {
  // 50 lines of code...
}

// ✅ Use - split into smaller functions
function validateUser(user) { }
function saveUser(user) { }
function sendEmail(user) { }
```

### 5. Use arrow functions for callbacks

```javascript
// ❌ Verbose
numbers.map(function(num) {
  return num * 2;
});

// ✅ Concise
numbers.map(num => num * 2);
```

---

## Summary

You've learned:
- ✅ Variables and data types
- ✅ Operators and control flow
- ✅ Functions and arrow functions
- ✅ Arrays and array methods
- ✅ Objects and object methods
- ✅ DOM manipulation
- ✅ Event handling
- ✅ Asynchronous JavaScript
- ✅ ES6+ features

**Next Steps:**
1. Practice with the JavaScript Exercises
2. Build small projects
3. Learn React for building user interfaces
4. Explore Node.js for backend development

Happy coding! 🚀sList.remove("hidden");
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
