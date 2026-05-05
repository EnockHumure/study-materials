# 🌐 The Complete Guide to APIs
### From Absolute Beginner to Advanced Mastery — With Real-Life Examples

---

## 📋 Table of Contents

1. [BEGINNER — Understanding the Basics](#beginner)
   - What is an API?
   - Real-Life Analogy
   - How APIs Work (The Request-Response Cycle)
   - Types of APIs
   - What is HTTP?
   - HTTP Methods (Verbs)
   - Status Codes
   - Your First API Call (No Code)
   - JSON — The Language of APIs

2. [INTERMEDIATE — Working with APIs](#intermediate)
   - REST APIs in Depth
   - Headers & Authentication
   - API Keys
   - Making API Calls with Code (Python & JavaScript)
   - Query Parameters & Filters
   - Pagination
   - Error Handling
   - Postman & Testing Tools
   - Rate Limiting

3. [ADVANCED — Building & Mastering APIs](#advanced)
   - Building Your Own REST API
   - Authentication Deep Dive (JWT, OAuth 2.0)
   - Webhooks vs Polling
   - GraphQL APIs
   - WebSockets & Real-Time APIs
   - API Versioning
   - Caching Strategies
   - Security Best Practices
   - API Documentation
   - Performance & Scaling

---

---

# 🟢 PART 1: BEGINNER {#beginner}

---

## 1. What is an API?

**API** stands for **Application Programming Interface**.

In the simplest terms: an API is a **messenger** that takes your request, goes and gets what you need, and brings it back to you.

> Think of it as a **waiter in a restaurant**. You (the customer) don't walk into the kitchen to make your food yourself. You tell the waiter what you want. The waiter goes to the kitchen (the server/backend) and brings your food (the data/result) back to you.

You are the **client**.  
The kitchen is the **server**.  
The waiter is the **API**.

---

## 2. Real-Life Analogy — The Restaurant

```
YOU (App / Browser)
      |
      |  "I want a pizza Margherita, please"
      ↓
   WAITER (API)
      |
      |  Carries your order to the kitchen
      ↓
  KITCHEN (Server / Database)
      |
      |  Prepares and returns pizza
      ↑
   WAITER (API)
      |
      |  Delivers the pizza back to you
      ↑
YOU (receive your pizza 🍕)
```

**More real-life API examples:**

| Situation | You (Client) | API | Server |
|---|---|---|---|
| Booking a flight on a travel site | Travel website | Flight search API | Airline database |
| Paying with card online | E-commerce site | Payment API (Stripe) | Bank |
| Logging in with Google | Any app | Google OAuth API | Google servers |
| Checking the weather on your phone | Weather app | Weather API | Weather database |
| Sending a WhatsApp message | WhatsApp app | WhatsApp API | Meta servers |

---

## 3. How APIs Work — The Request-Response Cycle

Every API interaction follows this same pattern:

```
Step 1: CLIENT sends a REQUEST
           ↓
Step 2: SERVER receives & processes it
           ↓
Step 3: SERVER sends back a RESPONSE
           ↓
Step 4: CLIENT uses the RESPONSE
```

**Real example — Google Maps in a food delivery app:**

1. You open the app and type your address → the app **requests** your location info from Google Maps API
2. Google Maps API receives the request and looks up your address
3. Google Maps sends back your coordinates (lat, long) as a **response**
4. The app displays a map pin at your location ✅

---

## 4. Types of APIs

There are several types of APIs you'll encounter:

### 4.1 Web APIs (Most Common)
APIs that work over the internet using HTTP. Examples: Twitter API, Spotify API, PayPal API.

### 4.2 REST APIs
The most popular style of web API. Uses standard HTTP methods. (Covered in depth later.)

### 4.3 GraphQL APIs
A newer approach where you ask for exactly the data you need. (Covered in advanced section.)

### 4.4 SOAP APIs
An older, more complex format. Still used in banking and enterprise systems.

### 4.5 WebSocket APIs
For real-time, two-way communication (e.g., live chat apps).

### 4.6 Internal vs External APIs

| Type | Description | Example |
|---|---|---|
| **Public/Open API** | Available to everyone | Twitter API, OpenWeather API |
| **Private/Internal API** | Used only within a company | Company's internal HR system |
| **Partner API** | Shared between specific partners | Uber sharing location with Google Maps |

---

## 5. What is HTTP?

**HTTP** = HyperText Transfer Protocol. It is the foundation of data communication on the web.

When you type `https://www.google.com` in your browser, you are making an **HTTP request** to Google's servers.

```
https://api.weather.com/v1/current?city=Kigali
  ↑         ↑              ↑           ↑
Protocol   Domain       Endpoint    Query param
```

### Breaking Down a URL:

| Part | Example | Meaning |
|---|---|---|
| **Protocol** | `https://` | How to communicate (secure HTTP) |
| **Domain** | `api.weather.com` | Which server to talk to |
| **Path/Endpoint** | `/v1/current` | Which specific resource to access |
| **Query Parameters** | `?city=Kigali` | Extra filters or options |

---

## 6. HTTP Methods (What Action Are You Doing?)

HTTP methods tell the server **what you want to do**. Think of them like actions at a library:

| HTTP Method | Library Analogy | What It Does |
|---|---|---|
| **GET** | "Can I read this book?" | Retrieve/read data |
| **POST** | "I want to add this new book" | Create new data |
| **PUT** | "Replace this book with a new edition" | Update (replace entire record) |
| **PATCH** | "Just fix the typo on page 5" | Update (partially modify) |
| **DELETE** | "Remove this book from the shelf" | Delete data |

### Real-Life Example — A Todo App:

```
GET    /todos           → Get the list of all todos
GET    /todos/1         → Get todo with ID 1
POST   /todos           → Create a new todo
PUT    /todos/1         → Replace todo #1 completely
PATCH  /todos/1         → Update just the title of todo #1
DELETE /todos/1         → Delete todo #1
```

---

## 7. HTTP Status Codes — What the Server Says Back

The server always responds with a **status code** telling you what happened.

### The 5 Categories:

| Range | Category | Feeling |
|---|---|---|
| 1xx | Informational | "Hold on, still working..." |
| 2xx | Success ✅ | "Done! Here's your result." |
| 3xx | Redirect | "It moved, go here instead." |
| 4xx | Client Error ❌ | "You made a mistake." |
| 5xx | Server Error 💥 | "We messed up on our end." |

### Most Common Status Codes:

| Code | Name | Real-Life Meaning |
|---|---|---|
| **200** | OK | Everything worked perfectly ✅ |
| **201** | Created | Your new item was created ✅ |
| **204** | No Content | Done, but nothing to return |
| **301** | Moved Permanently | The URL changed permanently |
| **400** | Bad Request | Your request had errors |
| **401** | Unauthorized | You need to log in first |
| **403** | Forbidden | You don't have permission |
| **404** | Not Found | That resource doesn't exist |
| **429** | Too Many Requests | You're sending too many requests |
| **500** | Internal Server Error | Something broke on the server |

> **Restaurant analogy for errors:**
> - 400: You ordered something that's not on the menu (bad request)
> - 401: You haven't introduced yourself yet (not authenticated)
> - 403: This section is VIP only (forbidden)
> - 404: That dish doesn't exist at this restaurant (not found)
> - 500: The kitchen is on fire (server error)

---

## 8. Your First API Call — No Code Required

You can call an API right now using just your browser!

### Try this (open in any browser):
```
https://api.github.com/users/octocat
```

You will see a **JSON response** about the GitHub user "octocat". That's an API call!

### Another one:
```
https://jsonplaceholder.typicode.com/posts/1
```

This returns a fake blog post. Notice the structure — that's **JSON**, which we'll cover next.

---

## 9. JSON — The Language of APIs

**JSON** = JavaScript Object Notation. It is the most common format APIs use to send and receive data.

Think of JSON like a **form you fill out**. It has field names and values.

### JSON Structure:

```json
{
  "name": "Alice",
  "age": 28,
  "city": "Kigali",
  "isStudent": false,
  "hobbies": ["coding", "reading", "hiking"],
  "address": {
    "street": "KN 5 Road",
    "country": "Rwanda"
  }
}
```

### JSON Data Types:

| Type | Example | Description |
|---|---|---|
| String | `"Hello"` | Text in quotes |
| Number | `42` or `3.14` | Numbers without quotes |
| Boolean | `true` or `false` | Yes/No values |
| Array | `["a", "b", "c"]` | List of items |
| Object | `{"key": "value"}` | Nested key-value pairs |
| Null | `null` | Empty / no value |

### Real API Response — Weather Example:

```json
{
  "city": "Kigali",
  "country": "RW",
  "temperature": {
    "current": 22,
    "feels_like": 21,
    "unit": "Celsius"
  },
  "weather": "Partly Cloudy",
  "humidity": 68,
  "wind_speed": 12,
  "forecast": [
    { "day": "Monday", "high": 25, "low": 18 },
    { "day": "Tuesday", "high": 24, "low": 17 }
  ]
}
```

---

---

# 🟡 PART 2: INTERMEDIATE {#intermediate}

---

## 10. REST APIs in Depth

**REST** = Representational State Transfer. It's a set of rules/conventions for designing web APIs.

### REST Principles:

1. **Stateless** — Each request is independent. The server doesn't remember previous requests.
   > Like ordering at a fast-food counter: each customer starts fresh; the cashier doesn't remember your last visit.

2. **Client-Server** — The client and server are separate. They only communicate via API.

3. **Uniform Interface** — Use standard HTTP methods and structured URLs.

4. **Resource-Based** — Everything is a "resource" (users, posts, products).

### REST URL Design Best Practices:

```
✅ GOOD REST URLs:
GET    /users                → Get all users
GET    /users/5              → Get user with ID 5
GET    /users/5/posts        → Get posts by user 5
POST   /users                → Create a new user
PUT    /users/5              → Update user 5
DELETE /users/5              → Delete user 5

❌ BAD REST URLs:
GET    /getUsers             (verb in URL — wrong!)
POST   /createNewUser        (verb in URL — wrong!)
GET    /users/getPostsByUser  (messy — wrong!)
```

---

## 11. Headers — Sending Extra Information

**Headers** are like the **envelope** of a letter. They carry extra information about the request or response.

```
Request Headers:
  Content-Type: application/json     ← "I'm sending JSON"
  Accept: application/json           ← "I want JSON back"
  Authorization: Bearer abc123token  ← "Here's my ID"
  User-Agent: MyApp/1.0              ← "I am this app"
```

### Common Request Headers:

| Header | Purpose | Example |
|---|---|---|
| `Content-Type` | Format of data you're sending | `application/json` |
| `Accept` | Format you want back | `application/json` |
| `Authorization` | Your credentials/token | `Bearer eyJhbG...` |
| `X-API-Key` | Your API key | `X-API-Key: abc123` |

---

## 12. Authentication — Proving Who You Are

Most real APIs require authentication. Here are the main methods:

### 12.1 API Keys (Most Common for Beginners)

An API key is like a **password for your app**.

```
Request to OpenWeather API:
GET https://api.openweathermap.org/data/2.5/weather?q=Kigali&appid=YOUR_API_KEY
```

You get this key after signing up. Keep it **secret** — never share it publicly!

### 12.2 Bearer Token (JWT)

A token you get after logging in. You send it in the header:

```
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

### 12.3 Basic Authentication

```
Authorization: Basic base64(username:password)
```

> Like showing your ID card + password at the door.

### 12.4 OAuth 2.0 (Login with Google/Facebook)

The most secure method. The user grants permission, and you get a token. (Covered in Advanced.)

---

## 13. Making API Calls with Code

### 13.1 Python — Using the `requests` Library

```python
# First install: pip install requests
import requests

# --- GET Request (Read Data) ---
response = requests.get("https://jsonplaceholder.typicode.com/posts/1")

print(response.status_code)   # 200
print(response.json())        # The JSON data as a Python dict

# --- GET with Parameters ---
params = {
    "q": "Kigali",
    "appid": "YOUR_API_KEY",
    "units": "metric"
}
response = requests.get("https://api.openweathermap.org/data/2.5/weather", params=params)
data = response.json()
print(f"Temperature in Kigali: {data['main']['temp']}°C")


# --- POST Request (Create Data) ---
new_post = {
    "title": "My First Post",
    "body": "Hello World from Rwanda!",
    "userId": 1
}
response = requests.post(
    "https://jsonplaceholder.typicode.com/posts",
    json=new_post  # Automatically sets Content-Type: application/json
)
print(response.status_code)  # 201 Created
print(response.json())


# --- With Authentication Headers ---
headers = {
    "Authorization": "Bearer YOUR_TOKEN_HERE",
    "Content-Type": "application/json"
}
response = requests.get("https://api.example.com/profile", headers=headers)
print(response.json())
```

### 13.2 JavaScript — Using `fetch` (Browser & Node.js)

```javascript
// --- GET Request ---
async function getPost() {
    const response = await fetch("https://jsonplaceholder.typicode.com/posts/1");
    
    if (!response.ok) {
        throw new Error(`HTTP error! Status: ${response.status}`);
    }
    
    const data = await response.json();
    console.log(data);
}

getPost();

// --- POST Request ---
async function createPost() {
    const response = await fetch("https://jsonplaceholder.typicode.com/posts", {
        method: "POST",
        headers: {
            "Content-Type": "application/json"
        },
        body: JSON.stringify({
            title: "Hello from Kigali",
            body: "Learning APIs is fun!",
            userId: 1
        })
    });
    
    const data = await response.json();
    console.log(data);   // { id: 101, title: "Hello from Kigali", ... }
}

createPost();

// --- With API Key in Header ---
async function getWeather(city) {
    const response = await fetch(
        `https://api.openweathermap.org/data/2.5/weather?q=${city}&units=metric`,
        {
            headers: {
                "X-API-Key": "YOUR_API_KEY_HERE"
            }
        }
    );
    
    const weather = await response.json();
    console.log(`${city}: ${weather.main.temp}°C`);
}

getWeather("Kigali");
```

---

## 14. Query Parameters — Filtering & Searching

Query parameters let you **filter, sort, or search** results without changing the endpoint.

They come after `?` in the URL, separated by `&`:

```
https://api.store.com/products?category=electronics&price_max=500&sort=rating&page=2
                                ↑                    ↑             ↑           ↑
                           Filter by               Max price    Sort order  Page number
```

### Common Query Parameter Patterns:

```
# Filtering
GET /users?role=admin
GET /products?category=shoes&color=red

# Searching
GET /articles?search=machine+learning

# Sorting
GET /products?sort=price&order=asc
GET /posts?sort=created_at&order=desc

# Pagination
GET /users?page=2&limit=20

# Date range
GET /orders?from=2024-01-01&to=2024-12-31

# Multiple values
GET /products?tags=python,api,web
```

---

## 15. Pagination — Handling Large Datasets

APIs rarely return thousands of records at once. They use pagination, like pages in a book.

### 15.1 Page-Based Pagination:

```
GET /posts?page=1&per_page=10   → Posts 1-10
GET /posts?page=2&per_page=10   → Posts 11-20
GET /posts?page=3&per_page=10   → Posts 21-30
```

Response often includes metadata:
```json
{
  "data": [ ... ],
  "pagination": {
    "current_page": 2,
    "total_pages": 15,
    "per_page": 10,
    "total_items": 147,
    "next": "/posts?page=3&per_page=10",
    "prev": "/posts?page=1&per_page=10"
  }
}
```

### 15.2 Cursor-Based Pagination (More Advanced):

```
GET /posts?cursor=eyJpZCI6MTB9&limit=10
```

Used by Twitter/X, Instagram APIs. More efficient for large, real-time datasets.

### 15.3 Python — Auto-Paging All Results:

```python
import requests

def get_all_posts():
    all_posts = []
    page = 1
    
    while True:
        response = requests.get(
            "https://api.example.com/posts",
            params={"page": page, "per_page": 50}
        )
        data = response.json()
        all_posts.extend(data["posts"])
        
        if page >= data["pagination"]["total_pages"]:
            break
        page += 1
    
    return all_posts
```

---

## 16. Error Handling — What to Do When Things Go Wrong

**Always handle errors.** APIs fail. Networks fail. Servers fail. Good code is prepared.

### Python Error Handling:

```python
import requests

def get_user(user_id):
    try:
        response = requests.get(
            f"https://api.example.com/users/{user_id}",
            timeout=10  # Don't wait forever
        )
        
        # Raise exception for 4xx and 5xx errors
        response.raise_for_status()
        
        return response.json()
    
    except requests.exceptions.Timeout:
        print("❌ Request timed out. The server took too long.")
        return None
    
    except requests.exceptions.ConnectionError:
        print("❌ No internet connection or server is down.")
        return None
    
    except requests.exceptions.HTTPError as e:
        status = e.response.status_code
        
        if status == 400:
            print("❌ Bad request. Check your data.")
        elif status == 401:
            print("❌ Unauthorized. Check your API key.")
        elif status == 403:
            print("❌ Forbidden. You don't have permission.")
        elif status == 404:
            print(f"❌ User {user_id} not found.")
        elif status == 429:
            print("⚠️ Rate limited! Wait before making more requests.")
        elif status >= 500:
            print("❌ Server error. Not your fault. Try again later.")
        return None
    
    except Exception as e:
        print(f"❌ Unexpected error: {e}")
        return None

# Usage
user = get_user(5)
if user:
    print(f"Found: {user['name']}")
else:
    print("Could not retrieve user.")
```

### JavaScript Error Handling:

```javascript
async function fetchUser(userId) {
    try {
        const response = await fetch(`https://api.example.com/users/${userId}`);
        
        if (!response.ok) {
            const error = await response.json();
            switch (response.status) {
                case 401: throw new Error("Unauthorized — check your token");
                case 404: throw new Error(`User ${userId} not found`);
                case 429: throw new Error("Rate limited — slow down!");
                case 500: throw new Error("Server error — try again later");
                default:  throw new Error(`HTTP Error ${response.status}: ${error.message}`);
            }
        }
        
        return await response.json();
        
    } catch (error) {
        if (error.name === "TypeError") {
            console.error("❌ Network error:", error.message);
        } else {
            console.error("❌ API error:", error.message);
        }
        return null;
    }
}
```

---

## 17. Postman — Testing APIs Without Writing Code

**Postman** is the most popular tool for testing APIs. Think of it as a **cockpit for APIs**.

### How to Use Postman:

1. **Download** Postman at [postman.com](https://postman.com)
2. **Create a new request**
3. **Choose your method**: GET, POST, PUT, DELETE
4. **Enter the URL**: `https://jsonplaceholder.typicode.com/users`
5. **Add headers** if needed (Authorization, Content-Type)
6. **Add body** for POST/PUT requests (JSON format)
7. **Click Send** ▶️
8. **Inspect the response**: status code, JSON body, timing

### Postman Environment Variables:

Instead of hardcoding your API key everywhere:
```
Variable: {{base_url}} = https://api.example.com
Variable: {{api_key}} = your_actual_key

Usage in URL: {{base_url}}/users?key={{api_key}}
```

---

## 18. Rate Limiting — APIs Have Traffic Rules

APIs limit how many requests you can make to prevent abuse.

### Common Rate Limit Headers:

```
X-RateLimit-Limit: 1000          ← Max requests allowed
X-RateLimit-Remaining: 543       ← Requests left this period
X-RateLimit-Reset: 1716905600    ← Unix timestamp when limit resets
Retry-After: 60                  ← Seconds to wait if you hit the limit
```

### Handling Rate Limits in Python:

```python
import requests
import time

def api_request_with_retry(url, max_retries=3):
    for attempt in range(max_retries):
        response = requests.get(url)
        
        if response.status_code == 200:
            return response.json()
        
        elif response.status_code == 429:
            # Check how long to wait
            retry_after = int(response.headers.get("Retry-After", 60))
            print(f"⚠️ Rate limited. Waiting {retry_after} seconds...")
            time.sleep(retry_after)
        
        else:
            print(f"❌ Error: {response.status_code}")
            break
    
    return None
```

### Rate Limiting Strategies:

```python
import time

# Strategy 1: Add small delays between requests
for user_id in range(1, 100):
    data = requests.get(f"/users/{user_id}").json()
    time.sleep(0.1)  # Wait 100ms between calls

# Strategy 2: Exponential backoff (double the wait time each retry)
def exponential_backoff(attempt):
    wait = 2 ** attempt  # 1s, 2s, 4s, 8s, 16s...
    time.sleep(wait)
```

---

---

# 🔴 PART 3: ADVANCED {#advanced}

---

## 19. Building Your Own REST API

Now you'll see what happens on the **other side** — the server.

### Using Python + Flask:

```python
# Install: pip install flask flask-restful

from flask import Flask, jsonify, request

app = Flask(__name__)

# In-memory "database" (for demo)
users = [
    {"id": 1, "name": "Alice", "email": "alice@example.com", "city": "Kigali"},
    {"id": 2, "name": "Bob",   "email": "bob@example.com",   "city": "Nairobi"},
]

# GET all users
@app.route("/users", methods=["GET"])
def get_users():
    city = request.args.get("city")  # Optional filter: /users?city=Kigali
    
    if city:
        filtered = [u for u in users if u["city"].lower() == city.lower()]
        return jsonify(filtered), 200
    
    return jsonify(users), 200

# GET single user
@app.route("/users/<int:user_id>", methods=["GET"])
def get_user(user_id):
    user = next((u for u in users if u["id"] == user_id), None)
    
    if not user:
        return jsonify({"error": "User not found"}), 404
    
    return jsonify(user), 200

# POST — create user
@app.route("/users", methods=["POST"])
def create_user():
    data = request.get_json()
    
    if not data or "name" not in data or "email" not in data:
        return jsonify({"error": "name and email are required"}), 400
    
    new_user = {
        "id": max(u["id"] for u in users) + 1,
        "name": data["name"],
        "email": data["email"],
        "city": data.get("city", "Unknown")
    }
    users.append(new_user)
    return jsonify(new_user), 201

# PUT — update user
@app.route("/users/<int:user_id>", methods=["PUT"])
def update_user(user_id):
    user = next((u for u in users if u["id"] == user_id), None)
    
    if not user:
        return jsonify({"error": "User not found"}), 404
    
    data = request.get_json()
    user.update(data)
    return jsonify(user), 200

# DELETE — remove user
@app.route("/users/<int:user_id>", methods=["DELETE"])
def delete_user(user_id):
    global users
    user = next((u for u in users if u["id"] == user_id), None)
    
    if not user:
        return jsonify({"error": "User not found"}), 404
    
    users = [u for u in users if u["id"] != user_id]
    return jsonify({"message": f"User {user_id} deleted"}), 200

if __name__ == "__main__":
    app.run(debug=True, port=5000)
```

### Test your API:
```bash
# Get all users
curl http://localhost:5000/users

# Get users in Kigali
curl http://localhost:5000/users?city=Kigali

# Create a user
curl -X POST http://localhost:5000/users \
  -H "Content-Type: application/json" \
  -d '{"name": "Carol", "email": "carol@rw.com", "city": "Musanze"}'

# Delete user
curl -X DELETE http://localhost:5000/users/1
```

---

## 20. Authentication Deep Dive

### 20.1 JWT — JSON Web Tokens

A JWT is a **signed token** that proves who you are. It has 3 parts:

```
eyJhbGciOiJIUzI1NiJ9.eyJ1c2VySWQiOjUsInJvbGUiOiJhZG1pbiJ9.Xq3lT...
       ↑                           ↑                              ↑
   Header (algorithm)          Payload (your data)           Signature
   (base64 encoded)            (base64 encoded)              (HMAC hash)
```

Decode the middle part and you get:
```json
{
  "userId": 5,
  "role": "admin",
  "iat": 1716900000,
  "exp": 1716986400
}
```

**JWT Flow:**
```
1. User logs in (POST /login with username + password)
2. Server verifies credentials
3. Server creates JWT: sign({userId: 5}, SECRET_KEY)
4. Server sends JWT back to client
5. Client stores JWT (localStorage or cookies)
6. Client sends JWT in every future request:
   Authorization: Bearer <token>
7. Server verifies JWT signature on each request
8. If valid → process request; if expired → 401 Unauthorized
```

### Flask JWT Implementation:

```python
# pip install flask-jwt-extended

from flask import Flask, jsonify, request
from flask_jwt_extended import (
    JWTManager, create_access_token,
    jwt_required, get_jwt_identity
)

app = Flask(__name__)
app.config["JWT_SECRET_KEY"] = "your-very-secret-key"  # Keep this secret!
jwt = JWTManager(app)

# Fake users DB
users_db = {"alice@example.com": {"password": "pass123", "id": 1, "name": "Alice"}}

# Login — get a token
@app.route("/login", methods=["POST"])
def login():
    email = request.json.get("email")
    password = request.json.get("password")
    
    user = users_db.get(email)
    if not user or user["password"] != password:
        return jsonify({"error": "Invalid credentials"}), 401
    
    # Create token valid for 24 hours
    token = create_access_token(identity=user["id"])
    return jsonify({"access_token": token}), 200

# Protected route — requires valid JWT
@app.route("/profile", methods=["GET"])
@jwt_required()
def profile():
    user_id = get_jwt_identity()  # Extract from token
    return jsonify({"user_id": user_id, "message": "Welcome!"}), 200
```

---

### 20.2 OAuth 2.0 — Login with Google

OAuth 2.0 lets users grant your app access to their data on another platform.

```
OAuth 2.0 Flow (Authorization Code):

1. User clicks "Login with Google" on your site
        ↓
2. Your app redirects to Google:
   https://accounts.google.com/o/oauth2/auth
     ?client_id=YOUR_CLIENT_ID
     &redirect_uri=https://yourapp.com/callback
     &scope=email profile
     &response_type=code
        ↓
3. User logs in on Google and approves permissions
        ↓
4. Google redirects back to YOUR site with a code:
   https://yourapp.com/callback?code=4/ABCDEF...
        ↓
5. Your server exchanges the code for tokens:
   POST https://oauth2.googleapis.com/token
   {code, client_id, client_secret, redirect_uri}
        ↓
6. Google returns:
   {
     "access_token": "ya29.xxx",      ← Use to call Google APIs
     "refresh_token": "1//xxx",       ← Use to get new access tokens
     "expires_in": 3600               ← Token valid for 1 hour
   }
        ↓
7. Your app calls Google's API with access_token to get user info
```

---

## 21. Webhooks vs Polling

### The Problem — How Does Your App Know When Something Happened?

**Scenario:** A customer just paid on your website. How does your app find out?

### Option 1: Polling (Asking Repeatedly)

```
Your app → "Did someone pay?" → Server: "No"
Your app → "Did someone pay?" → Server: "No"
Your app → "Did someone pay?" → Server: "No"
Your app → "Did someone pay?" → Server: "YES! Order #456 paid"
```

Like repeatedly calling a restaurant to ask: "Is my table ready?"

```python
# Polling example
import time
import requests

def poll_for_payment(order_id):
    while True:
        response = requests.get(f"/orders/{order_id}")
        if response.json()["status"] == "paid":
            print("Payment received!")
            break
        time.sleep(5)  # Check every 5 seconds
```

**Cons:** Wastes bandwidth. Slow. Server strain.

### Option 2: Webhooks (Server Notifies You)

```
[Payment happens]
       ↓
Stripe Server → POST your-app.com/webhooks/payment → Your app: "Got it!"
```

Like the restaurant texting you "Your table is ready!" instead of you calling them.

```python
# Webhook receiver in Flask
@app.route("/webhooks/stripe", methods=["POST"])
def handle_stripe_webhook():
    payload = request.get_json()
    event_type = payload.get("type")
    
    if event_type == "payment_intent.succeeded":
        amount = payload["data"]["object"]["amount"]
        customer = payload["data"]["object"]["customer"]
        print(f"✅ Payment of ${amount/100} received from {customer}")
        
        # Do something: update DB, send email, etc.
        send_confirmation_email(customer)
    
    elif event_type == "payment_intent.payment_failed":
        print("❌ Payment failed — notify customer")
    
    return jsonify({"received": True}), 200  # Always return 200!
```

| | Polling | Webhooks |
|---|---|---|
| **Who initiates?** | Client asks repeatedly | Server pushes when event occurs |
| **Latency** | High (depends on interval) | Near real-time |
| **Resource use** | High (many requests) | Low (only when needed) |
| **Complexity** | Simple to implement | Need public URL + event handling |
| **Best for** | Simple checks, small scale | Payment, notifications, real-time events |

---

## 22. GraphQL APIs

GraphQL is a query language for APIs. Instead of many endpoints, there's ONE endpoint, and you ask for exactly the data you need.

### REST vs GraphQL Problem:

```
// REST — Over-fetching (you get TOO MUCH data)
GET /users/1
Returns: {id, name, email, address, phone, created_at, updated_at, ...}
         ↑ You only wanted the name!

// REST — Under-fetching (you need MULTIPLE requests)
GET /users/1            → Get user
GET /users/1/posts      → Get their posts
GET /users/1/followers  → Get their followers
         ↑ 3 requests for data you need at once!
```

### GraphQL Solution — Ask for Exactly What You Need:

```graphql
# Query — read data
query {
  user(id: 1) {
    name
    posts(last: 3) {
      title
      publishedAt
    }
    followersCount
  }
}
```

Response — only what you asked for:
```json
{
  "data": {
    "user": {
      "name": "Alice",
      "posts": [
        { "title": "Learning APIs", "publishedAt": "2024-11-10" },
        { "title": "Rwanda Tech Scene", "publishedAt": "2024-10-20" }
      ],
      "followersCount": 1523
    }
  }
}
```

### GraphQL Mutations (Write Data):

```graphql
mutation {
  createPost(input: {
    title: "GraphQL is Amazing"
    body: "Here's why..."
    authorId: 1
  }) {
    id
    title
    createdAt
  }
}
```

### Calling GraphQL from Python:

```python
import requests

GRAPHQL_URL = "https://api.example.com/graphql"

query = """
query GetUser($userId: ID!) {
  user(id: $userId) {
    name
    email
    posts {
      title
    }
  }
}
"""

response = requests.post(
    GRAPHQL_URL,
    json={
        "query": query,
        "variables": {"userId": "1"}
    },
    headers={"Authorization": "Bearer YOUR_TOKEN"}
)

data = response.json()
user = data["data"]["user"]
print(f"User: {user['name']} has {len(user['posts'])} posts")
```

---

## 23. WebSockets — Real-Time Communication

HTTP is a one-way street. You ask → Server answers → Connection closes.

**WebSockets** keep the connection open, enabling two-way real-time communication.

```
HTTP (Traditional):
Client: "Give me messages"  → Server: "Here: [message1]" → connection closes
Client: "Give me messages"  → Server: "Here: [message2]" → connection closes
Client: "Give me messages"  → Server: "Here: [message3]" → connection closes

WebSocket (Real-time):
Client: "Open connection" ↔ Server: "Connected!"
         ← Message from Alice received! (server pushes)
         ← Message from Bob received!  (server pushes)
Client: "Hi everyone!" →                (client pushes)
         ← 3 people liked your message (server pushes)
         ...connection stays open...
```

### JavaScript WebSocket (Chat App):

```javascript
// Connect to WebSocket server
const socket = new WebSocket("wss://chat.example.com/room/1");

// Connection opened
socket.addEventListener("open", () => {
    console.log("✅ Connected to chat room");
    socket.send(JSON.stringify({
        type: "join",
        username: "Alice"
    }));
});

// Listen for messages
socket.addEventListener("message", (event) => {
    const data = JSON.parse(event.data);
    
    if (data.type === "message") {
        displayMessage(data.username, data.text);
    } else if (data.type === "user_joined") {
        displayNotification(`${data.username} joined the room`);
    }
});

// Send a message
function sendMessage(text) {
    socket.send(JSON.stringify({
        type: "message",
        text: text
    }));
}

// Connection closed
socket.addEventListener("close", () => {
    console.log("❌ Disconnected from chat");
});
```

---

## 24. API Versioning

When you update an API, you can't break apps already using it. Versioning lets old and new clients coexist.

### Versioning Strategies:

```
# 1. URL Versioning (Most Common)
GET /v1/users       ← Old version (still works)
GET /v2/users       ← New version with new features

# 2. Header Versioning
GET /users
Headers: API-Version: 2

# 3. Query Parameter
GET /users?version=2
```

### Flask Versioned API:

```python
from flask import Flask, Blueprint, jsonify

app = Flask(__name__)

# Version 1 blueprint
v1 = Blueprint("v1", __name__, url_prefix="/v1")

@v1.route("/users")
def get_users_v1():
    return jsonify({"users": [{"id": 1, "name": "Alice"}]})

# Version 2 blueprint (with new fields)
v2 = Blueprint("v2", __name__, url_prefix="/v2")

@v2.route("/users")
def get_users_v2():
    return jsonify({
        "users": [{"id": 1, "name": "Alice", "avatar_url": "...", "verified": True}],
        "pagination": {"total": 1}
    })

app.register_blueprint(v1)
app.register_blueprint(v2)
```

---

## 25. Caching — Don't Fetch the Same Data Twice

Caching saves responses so you don't have to call the API again for the same data.

```
Without cache:
Request → API → Response  (takes 200ms, costs API call)
Request → API → Response  (takes 200ms, costs API call)
Request → API → Response  (takes 200ms, costs API call)

With cache:
Request → API → Response → Save to cache  (200ms)
Request → Cache hit!      (1ms) ← same data, no API call
Request → Cache hit!      (1ms) ← 
```

### HTTP Cache Headers:

```
Response Headers:
Cache-Control: max-age=3600       ← Cache for 1 hour
ETag: "abc123"                     ← Fingerprint of the data
Last-Modified: Mon, 05 May 2025   ← When it was last changed

Request Headers (after expiry):
If-None-Match: "abc123"            ← "Is data still the same?"
If-Modified-Since: Mon, 05 May    ← "Has it changed since?"

Server Response if unchanged:
304 Not Modified                   ← Use your cached copy!
```

### Python Caching with `requests-cache`:

```python
# pip install requests-cache
import requests_cache

# Cache all requests for 1 hour
requests_cache.install_cache("api_cache", expire_after=3600)

import requests

# This call hits the API once, then uses cache for 1 hour
response = requests.get("https://api.openweathermap.org/weather?q=Kigali")
print(f"From cache: {response.from_cache}")  # False first time
response = requests.get("https://api.openweathermap.org/weather?q=Kigali")
print(f"From cache: {response.from_cache}")  # True second time!
```

---

## 26. Security Best Practices

### 26.1 Never Expose API Keys

```python
# ❌ WRONG — key in source code
api_key = "sk_live_abc123XYZ"

# ✅ CORRECT — key in environment variable
import os
api_key = os.environ.get("API_KEY")
```

```bash
# Set in terminal (Linux/Mac)
export API_KEY="sk_live_abc123XYZ"

# Or use a .env file (never commit to git!)
echo "API_KEY=sk_live_abc123XYZ" >> .env
```

### 26.2 Input Validation

```python
@app.route("/users", methods=["POST"])
def create_user():
    data = request.get_json()
    
    # Validate required fields
    required = ["name", "email", "password"]
    missing = [f for f in required if f not in data]
    if missing:
        return jsonify({"error": f"Missing fields: {missing}"}), 400
    
    # Validate email format
    import re
    if not re.match(r"[^@]+@[^@]+\.[^@]+", data["email"]):
        return jsonify({"error": "Invalid email format"}), 400
    
    # Validate string lengths
    if len(data["name"]) > 100:
        return jsonify({"error": "Name too long (max 100 chars)"}), 400
    
    # ... proceed
```

### 26.3 HTTPS Always

```
✅ https://api.example.com/users    ← Encrypted, secure
❌ http://api.example.com/users     ← Plain text, anyone can read it
```

### 26.4 CORS — Cross-Origin Resource Sharing

Controls which websites can call your API:

```python
# pip install flask-cors
from flask_cors import CORS

app = Flask(__name__)

# Allow only specific origins
CORS(app, origins=["https://yourfrontend.com", "https://admin.yourapp.com"])

# Allow all (only for development!)
CORS(app, origins="*")
```

### 26.5 Rate Limiting Your Own API:

```python
# pip install flask-limiter
from flask_limiter import Limiter

limiter = Limiter(app, key_func=lambda: request.remote_addr)

@app.route("/api/data")
@limiter.limit("100 per hour")   # Max 100 requests per hour per IP
def get_data():
    return jsonify({"data": "..."})
```

---

## 27. API Documentation

Good documentation is what separates a usable API from an unusable one.

### OpenAPI / Swagger — The Standard:

```yaml
# openapi.yaml
openapi: "3.0.0"
info:
  title: "User Management API"
  version: "1.0.0"
  description: "API for managing users"

servers:
  - url: "https://api.example.com/v1"

paths:
  /users:
    get:
      summary: "Get all users"
      parameters:
        - name: city
          in: query
          schema:
            type: string
          description: "Filter by city"
      responses:
        "200":
          description: "List of users"
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: "#/components/schemas/User"

components:
  schemas:
    User:
      type: object
      required: [id, name, email]
      properties:
        id:
          type: integer
          example: 1
        name:
          type: string
          example: "Alice"
        email:
          type: string
          format: email
          example: "alice@example.com"
```

### Auto-Generate Docs with Flask:

```python
# pip install flask-swagger-ui apispec

from apispec import APISpec
from apispec.ext.marshmallow import MarshmallowPlugin
from flask_swagger_ui import get_swaggerui_blueprint

# Swagger UI available at: http://localhost:5000/docs
SWAGGER_URL = "/docs"
API_URL = "/static/openapi.json"
swaggerui_blueprint = get_swaggerui_blueprint(SWAGGER_URL, API_URL)
app.register_blueprint(swaggerui_blueprint)
```

---

## 28. Performance & Scaling

### 28.1 Async Requests — Do Many at Once

```python
# pip install aiohttp
import asyncio
import aiohttp

# Sequential (slow) — one after another
async def fetch_sequential(user_ids):
    results = []
    async with aiohttp.ClientSession() as session:
        for uid in user_ids:
            async with session.get(f"/users/{uid}") as resp:
                results.append(await resp.json())
    return results

# Concurrent (fast) — all at the same time!
async def fetch_concurrent(user_ids):
    async with aiohttp.ClientSession() as session:
        tasks = [session.get(f"/users/{uid}") for uid in user_ids]
        responses = await asyncio.gather(*tasks)
        results = [await r.json() for r in responses]
    return results

# 100 requests:
# Sequential: ~10 seconds
# Concurrent: ~0.5 seconds ← 20x faster!
asyncio.run(fetch_concurrent(range(1, 101)))
```

### 28.2 Connection Pooling:

```python
import requests
from requests.adapters import HTTPAdapter

session = requests.Session()

# Reuse connections — much faster for many requests
adapter = HTTPAdapter(
    pool_connections=10,   # 10 connection pools
    pool_maxsize=50,        # 50 connections per pool
    max_retries=3           # Auto-retry on failure
)
session.mount("https://", adapter)

# Now use session instead of requests.get(...)
response = session.get("https://api.example.com/data")
```

### 28.3 Compression:

```python
# Request compressed responses (saves bandwidth)
headers = {
    "Accept-Encoding": "gzip, deflate, br"
}
response = requests.get("https://api.example.com/large-data", headers=headers)
# requests automatically decompresses gzip for you!
```

---

## 29. Real-World Project — Complete Example

Let's build a **Currency Converter** that uses a real API:

```python
import requests
import os
from datetime import datetime

API_KEY = os.environ.get("EXCHANGE_RATE_API_KEY", "demo")
BASE_URL = "https://v6.exchangerate-api.com/v6"

def get_exchange_rates(base_currency="USD"):
    """Fetch current exchange rates."""
    url = f"{BASE_URL}/{API_KEY}/latest/{base_currency}"
    
    response = requests.get(url, timeout=10)
    response.raise_for_status()
    data = response.json()
    
    if data["result"] != "success":
        raise ValueError(f"API Error: {data.get('error-type', 'Unknown')}")
    
    return data["conversion_rates"]

def convert_currency(amount, from_currency, to_currency):
    """Convert amount between currencies."""
    rates = get_exchange_rates(from_currency)
    
    if to_currency not in rates:
        raise ValueError(f"Unknown currency: {to_currency}")
    
    converted = amount * rates[to_currency]
    return round(converted, 2)

def currency_menu():
    """Interactive currency converter."""
    print("🌍 Currency Converter")
    print("=" * 40)
    
    from_cur = input("From currency (e.g. USD): ").strip().upper()
    to_cur   = input("To currency (e.g. RWF):   ").strip().upper()
    amount   = float(input(f"Amount in {from_cur}: "))
    
    result = convert_currency(amount, from_cur, to_cur)
    print(f"\n✅ {amount} {from_cur} = {result:,.2f} {to_cur}")
    print(f"   Rate fetched at: {datetime.now().strftime('%H:%M:%S')}")

if __name__ == "__main__":
    currency_menu()
```

---

## 30. Quick Reference Cheat Sheet

### HTTP Methods Summary:
```
GET    → Read        → /users, /users/1
POST   → Create      → /users (body: user data)
PUT    → Replace     → /users/1 (body: full user)
PATCH  → Update part → /users/1 (body: {name: "new name"})
DELETE → Remove      → /users/1
```

### Status Codes to Know:
```
200 OK               → Success
201 Created          → POST success
204 No Content       → DELETE success
400 Bad Request      → You sent bad data
401 Unauthorized     → Need to authenticate
403 Forbidden        → Authenticated but no permission
404 Not Found        → Resource doesn't exist
429 Too Many Req.    → Rate limited
500 Server Error     → Not your fault
```

### API Security Checklist:
```
☐ Use HTTPS only
☐ Never commit API keys to git
☐ Use environment variables for secrets
☐ Validate all input
☐ Implement rate limiting
☐ Use authentication (JWT or OAuth)
☐ Enable CORS only for allowed origins
☐ Log and monitor API usage
☐ Version your API
☐ Document everything
```

---

## 31. Learning Path & Resources

### Beginner (Start Here):
- Practice at: [jsonplaceholder.typicode.com](https://jsonplaceholder.typicode.com)
- Free APIs: [public-apis.io](https://public-apis.io)
- Test tool: [Postman](https://postman.com)

### Intermediate:
- Build APIs: Flask (Python), Express.js (Node)
- Auth: JWT.io debugger at [jwt.io](https://jwt.io)
- Docs: OpenAPI Specification

### Advanced:
- GraphQL: [graphql.org](https://graphql.org)
- Real-time: WebSockets with Socket.IO
- API Design: REST API Design Rulebook (O'Reilly)

### Free APIs to Practice With:
| API | What It Does | URL |
|---|---|---|
| JSONPlaceholder | Fake data for testing | jsonplaceholder.typicode.com |
| OpenWeather | Weather data | openweathermap.org/api |
| GitHub | Repos, users, code | api.github.com |
| REST Countries | Country data | restcountries.com |
| PokeAPI | Pokémon data | pokeapi.co |
| CoinGecko | Crypto prices | coingecko.com/api |

---

*This guide covers APIs from absolute beginner to advanced level.*
*Keep practicing — the best way to learn APIs is to build with them!* 🚀
