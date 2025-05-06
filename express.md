# Express.js and Web Frameworks Cheat Sheet

> **How to use this guide:**  
> Start at the top for a full, step-by-step foundation, or jump to any section for focused reference. Each topic includes explanations, code samples, and pro tips.

---

## 1. What is Express.js? What Does It “Express”?

**Express.js** is a web framework for Node.js.  
A web framework like Express “expresses” your code as a web server, making it easy to respond to HTTP requests (web traffic) with routes, middleware, and logic.

**Why use Express (or any web framework)?**
- Manages HTTP requests and responses.
- Simplifies routing (URLs to code).
- Makes middleware (reusable logic, like authentication or logging) easy.
- Helps serve files, handle forms, connect to databases, and more.

**Alternatives to Express:**
- **Fastify** (faster, similar API)
- **Koa** (by the same creators, more minimal)
- **Hapi** (configuration-driven)
- **NestJS** (full-featured, uses TypeScript, OOP style)
- **Plain Node.js** (no framework, more code for same tasks)

**But in most beginner/intermediate classrooms, Express is the standard.**

---

## 2. Installing and Setting Up Express

**Step 1: Make a project folder and initialize NPM**

```bash
mkdir my-express-app
cd my-express-app
npm init -y
```

**Step 2: Install Express**

```bash
npm install express
```

**Step 3: Create your app entry file (`app.js` or `server.js`)**

```js
// app.js
const express = require('express');
const app = express();

const PORT = 3000; // or use process.env.PORT for deployment

// Example route
app.get('/', (req, res) => {
  res.send('Hello, Express!');
});

// Start server
app.listen(PORT, () => {
  console.log(`Server running at http://localhost:${PORT}`);
});
```

**Step 4: Run your server**

```bash
node app.js
```

---

## 3. How Express Works: Basics

### Routing (Handling URLs and Verbs)

```js
// GET request to homepage
app.get('/', (req, res) => { ... });

// POST request to /data
app.post('/data', (req, res) => { ... });

// Route with a URL parameter
app.get('/user/:id', (req, res) => {
  res.send(`User ID: ${req.params.id}`);
});
```

### Request and Response Objects

- `req` – incoming data (params, query, body, headers, etc.)
- `res` – how you reply (send data, set status, redirect, etc.)

### Query Strings and Params

```js
// GET /search?term=express
app.get('/search', (req, res) => {
  res.send(req.query.term); // "express"
});
```

---

## 4. Middleware

**Middleware** are functions that run during the request–response cycle.  
They can modify `req` or `res`, end the request, or call `next()` to continue.

### Built-in Middleware

- **Parse JSON bodies**:
  ```js
  app.use(express.json());
  ```
- **Parse URL-encoded form bodies**:
  ```js
  app.use(express.urlencoded({ extended: true }));
  ```
- **Serve static files**:
  ```js
  app.use(express.static('public'));
  ```

### Custom Middleware Example

```js
app.use((req, res, next) => {
  console.log(`${req.method} ${req.url}`);
  next();
});
```

---

## 5. Sending Responses

```js
res.send('Hello!');                       // Send plain text or HTML
res.json({ key: 'value' });               // Send JSON
res.status(404).send('Not found');        // Set status and send message
res.sendFile(__dirname + '/index.html');  // Send a file
res.redirect('/other');                   // Redirect to another route
```

---

## 6. Handling POST Data (Forms, JSON)

### Parsing JSON Data

```js
app.use(express.json());

app.post('/api/data', (req, res) => {
  console.log(req.body); // { key: value }
  res.json({ received: req.body });
});
```

### Parsing Form Data

```js
app.use(express.urlencoded({ extended: true }));

app.post('/submit', (req, res) => {
  console.log(req.body); // { username: '...', password: '...' }
  res.send('Form received!');
});
```

---

## 7. Route Organization with Routers

**Split routes into files using the Router class for maintainability.**

**users.js**
```js
const express = require('express');
const router = express.Router();

router.get('/', (req, res) => res.send('All users'));
router.get('/:id', (req, res) => res.send(`User ${req.params.id}`));

module.exports = router;
```

**app.js**
```js
const usersRouter = require('./users');
app.use('/users', usersRouter); // Mount at /users
```

---

## 8. Error Handling

### 404 Handler (at the end of all routes)

```js
app.use((req, res) => {
  res.status(404).send('404 Not Found');
});
```

### General Error Handler

```js
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
```

---

## 9. Using Third-Party Middleware

**Install with npm, then `require` and `app.use()`.**

```bash
npm install morgan cors
```

```js
const morgan = require('morgan');
const cors = require('cors');

app.use(morgan('dev')); // HTTP request logging
app.use(cors());        // Enable CORS
```

---

## 10. Environment Variables (dotenv)

**Keep secrets and config out of your code.**

```bash
npm install dotenv
```

**In your app:**
```js
require('dotenv').config();
const PORT = process.env.PORT || 3000;
```

**In `.env` file:**
```
PORT=4000
SECRET=mysecret
```

---

## 11. Async/Await Routes

```js
app.get('/data', async (req, res, next) => {
  try {
    const data = await someAsyncFunction();
    res.json(data);
  } catch (err) {
    next(err); // Passes to error handler
  }
});
```

---

## 12. Common Pitfalls

- **Order matters:** Middleware and routes run in order defined.
- **Missing body parser:** Use `express.json()` or `express.urlencoded()` before using `req.body`.
- **Not calling `next()`:** Custom middleware must call `next()` or requests will hang.
- **Port in use:** If server won’t start, port might already be in use (`EADDRINUSE`).

---

## 13. Alternatives to Express

- **Fastify:** Similar to Express, but faster and with built-in validation.
- **Koa:** By the original Express creators, more minimal, async/await-first.
- **Hapi:** Configuration-focused, powerful for large apps.
- **NestJS:** Uses TypeScript, OOP style, inspired by Angular.
- **Plain Node.js HTTP:** No framework; more boilerplate for routing, middleware, etc.

**Why stick with Express for now:**  
- Most tutorials, classroom content, and starter projects use Express.
- Huge ecosystem and community.
- Simple API, but powerful enough for real projects.

---

## 14. Practice Project Ideas

- REST API for a to-do list (CRUD)
- Blog backend: serve posts, comments, users
- Authentication system (sessions, JWT)
- Serve an HTML/CSS/JS website with API endpoints

---

## 15. Further Resources

- [Express.js Official Documentation](https://expressjs.com/)
- [MDN: Express/Node.js Tutorial](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs)
- [Node.js Official Docs](https://nodejs.org/en/docs)
- [Awesome Express GitHub](https://github.com/expressjs/express#community)

---

