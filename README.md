# Node.js Express Web Server Architecture Guide

![Project Type](https://img.shields.io/badge/Project%20Type-Backend%20Learning%20Case%20Study-purple)
![Node.js](https://img.shields.io/badge/Node.js-18+-green)
![Express](https://img.shields.io/badge/Framework-Express-black)
![REST](https://img.shields.io/badge/API-REST-blue)
![Middleware](https://img.shields.io/badge/Pattern-Middleware-orange)
![Security](https://img.shields.io/badge/Security-Helmet%20%2B%20CORS-red)
![HTTP](https://img.shields.io/badge/Protocol-HTTP-lightgrey)
![Architecture](https://img.shields.io/badge/Architecture-Web%20Server-purple)

---

# Express.js Web Server Architecture

This repository demonstrates how to build a **modern web server using Node.js and Express**.

The project explains the architecture behind:

- HTTP request handling
- middleware pipelines
- static content delivery
- request parsing
- security headers
- REST endpoint design

It can be used as a **learning reference for backend developers building APIs with Express.js**.

---

# Case Study

## Problem

Many developers learn Express through small code snippets but struggle to understand:

- how request pipelines work
- middleware chaining
- request parsing
- static file serving
- security middleware
- response handling

Without understanding these layers, backend applications become hard to maintain.

---

## Solution

This repository demonstrates a **step-by-step architecture for building an Express application**, including:

- HTTP server setup
- routing structure
- middleware pipeline
- request parsing
- static assets
- security middleware
- response management

The project also explains **how Express processes requests internally**.

---

# Architecture

Typical request lifecycle demonstrated in this project:

```text

Client
│
▼
HTTP Request
│
▼
Express Server
│
├── Logger Middleware
│
├── Body Parser
│
├── Static File Middleware
│
├── Security Middleware (Helmet)
│
├── CORS Middleware
│
▼
Route Handler
│
▼
Response Object
│
▼
Client Response

```

This layered pipeline allows developers to **modularize application logic**.

---

# Folder Structure

Example project structure used in this guide.

```text
express-app
│
├── public
│ └── index.html
│
├── index.js
│
├── package.json
│
└── README.md
```


### public/

Contains static assets served directly by the server.

Example:

- HTML pages
- CSS files
- images
- client-side JavaScript

---

# Key Concepts Covered

This project demonstrates several core backend concepts.

### HTTP Server

Basic Express server initialization.

### Routing

Handling different HTTP endpoints.

### Middleware

Request processing pipeline.

### Static File Serving

Serving frontend assets.

### Request Parsing

Handling JSON and URL encoded payloads.

### Security Middleware

Using Helmet and CORS.

### HTTP Response Objects

Understanding Express response methods.

---

# Creating the Application

## 1 Initialize the Node.js project
```bash
npm init -y
```

---

## 2 Install Express
```bash
npm install express
```

---

## 3 Create the server file

Create a file:
```bash
index.js
```


Example server:

```js
const express = require('express');

const app = express();

app.get('/', (req, res) => {
  res.send("Hello World Node.js community!");
});

const PORT = 3000;

app.listen(PORT, () => {
  console.log(`Server running at http://localhost:${PORT}`);
});
```

# Middleware Architecture

Express middleware allows request processing before reaching route handlers.

Example logging middleware:

```js
app.use((req, res, next) => {

console.log(new Date().toLocaleDateString(), req.method, req.path);

next();

});
```
Middleware enables:

authentication

validation

logging

security filters

# Static File Middleware

Serving static files from the public directory.
```js
app.use(express.static('public'));
```

Example:
```bash
http://localhost:3000/index.html
```
Express automatically returns the file.

# Request Parsing

Express provides built-in middleware for request bodies.

## JSON parsing
```js
app.use(express.json());
```
## URL encoded parsing
```js
app.use(express.urlencoded({ extended: true }));
```
app.use(express.urlencoded({ extended: true }));
```bash
req.body
```
# Security Middleware
Helmet
Adds security HTTP headers:
```bash
npm install helmet
```
```js
const helmet = require('helmet');

app.use(helmet());
```
Helmet protects against:

clickjacking

MIME sniffing

XSS attacks

# CORS

Allows controlled cross-origin access:
```bash
npm install cors
```
```js
const cors = require('cors');
app.use(cors());
```
# Express Response Methods

Express provides powerful response helpers.

Examples used in this project.

JSON response:
```js
res.json({message: "Example JSON response"});
```

File download
```js
res.download(filePath);
```

Redirect
```js
res.redirect("https://example.com");
```

Send file
```js
res.sendFile(path.join(__dirname, filePath));
```

# Express Request Object

Important properties used by backend APIs.

Path parameters
```bash
req.params
```

Example:
```bash
/products/:id
```

# Query parameters
```bash
req.query
```
Example:
```bash
/products?sort=desc
```

# Request body
```bash
req.body
```
Used in POST / PUT requests.

# Running the Project
Clone the repository:
```bash
git clone https://github.com/your-repository
```
Install dependencies:
```bash
npm install
```
Run the server:
```bash
node index.js
```
Open in browser:
```bash
http://localhost:3000
```

---

# Learning Outcomes

Developers studying this repository will understand:

Express server architecture

middleware pipelines

request lifecycle

static file serving

security middleware

HTTP request / response objects

---

# Technologies

Node.js

Express.js

Helmet

CORS

HTTP

REST

---

# Author

Thiago Reis Lima

LinkedIn:
```bash
https://www.linkedin.com/in/thiago-lima-2a5896166/
```
