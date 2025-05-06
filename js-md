# JavaScript Cheat Sheet: Beginner to Advanced

> **How to use this guide:**  
> Start from the top for a structured path, or jump to any section for reference. Each topic includes explanations, code samples, and pro tips.

---

## 1. Getting Started with JavaScript

### What is JavaScript?
JavaScript is a high-level programming language that brings interactivity and dynamic features to web pages. It runs in all major browsers and on servers (Node.js).

### Ways to Add JavaScript to Your Web Page

- **Inline JavaScript** (not recommended for organization or security):  
  ```html
  <button onclick="alert('Hello!')">Click me</button>
  ```

- **Internal JavaScript** (inside your HTML file):  
  ```html
  <script>
    console.log('Hello from internal JS!');
  </script>
  ```

- **External JavaScript** (best practice):  
  ```html
  <script src="script.js"></script>
  ```
  > Place the `<script>` tag right before `</body>` for best performance.

---

## 2. Comments & Debugging

- **Single-line:**  
  ```js
  // This is a single-line comment
  ```

- **Multi-line:**  
  ```js
  /* This is a
     multi-line comment */
  ```

- **Debugging:**  
  Use `console.log(value)` to display values in the browser console.

---

## 3. Variables & Data Types

### Declaring Variables

- `let` (block-scoped, value can change):  
  ```js
  let age = 30;
  ```

- `const` (block-scoped, value cannot be reassigned):  
  ```js
  const name = "Alice";
  ```

- `var` (function-scoped, avoid using in modern JS):  
  ```js
  var oldWay = true;
  ```

### Data Types

- **String:** `"hello"`, `'world'`, `` `template` ``
- **Number:** `42`, `3.14`, `-7`
- **Boolean:** `true`, `false`
- **Array:** `[1, 2, 3]`, `["a", "b"]`
- **Object:** `{ name: "Alice", age: 25 }`
- **Null:** `null` (intentional absence of value)
- **Undefined:** `undefined` (variable declared but not assigned)
- **Symbol:** `Symbol("id")` (unique identifier, advanced)
- **BigInt:** `12345678901234567890n` (for very large integers, advanced)

### Type Checking
```js
typeof "Hello";   // "string"
typeof 42;        // "number"
typeof [1,2,3];   // "object"
typeof null;      // "object" (historical JS quirk)
typeof undefined; // "undefined"
```

---

## 4. Operators

- **Arithmetic:** `+`, `-`, `*`, `/`, `%` (modulus), `**` (exponent)
- **Assignment:** `=`, `+=`, `-=`, `*=`, `/=`
- **Comparison:** `==` (loose), `===` (strict), `!=`, `!==`, `>`, `<`, `>=`, `<=`
- **Logical:** `&&` (and), `||` (or), `!` (not)
- **Concatenation:** `"Hello" + " world"` → `"Hello world"`
- **Ternary:**  
  ```js
  let result = age >= 18 ? "Adult" : "Minor";
  ```

---

## 5. Strings

```js
let str = "hello";
let len = str.length;              // 5
let upper = str.toUpperCase();     // "HELLO"
let lower = str.toLowerCase();     // "hello"
let part = str.slice(1, 3);        // "el"
let joined = "Hello, " + name + "!";      // "Hello, Alice!"
let templ = `Hi, ${name}. Age: ${age}`;   // Template literals
let includes = str.includes('el');        // true
let replaced = str.replace("el", "OL");   // "hOLlo"
```

---

## 6. Numbers & Math

```js
let n = 3.14159;
Math.round(n);      // 3
Math.floor(n);      // 3
Math.ceil(n);       // 4
Math.max(4, 7, 1);  // 7
Math.min(4, 7, 1);  // 1
Math.random();      // 0 <= x < 1
parseInt("42");     // 42
parseFloat("3.14"); // 3.14
(5).toString();     // "5"
```

---

## 7. Arrays

```js
const fruits = ["apple", "banana", "orange"];
fruits[0];                // "apple"
fruits.length;            // 3

fruits.push("grape");     // Add to end
fruits.pop();             // Remove from end
fruits.unshift("lemon");  // Add to start
fruits.shift();           // Remove from start

fruits.forEach(fruit => console.log(fruit)); // Loop through all

const newFruits = fruits.map(fruit => fruit.toUpperCase()); // Transform
const longFruits = fruits.filter(fruit => fruit.length > 5); // Filter
const hasBanana = fruits.includes("banana"); // true
const found = fruits.find(fruit => fruit.startsWith("a")); // "apple"
const index = fruits.indexOf("banana"); // 1
```

---

## 8. Objects

```js
const person = {
  name: "Alice",
  age: 25,
  greet: function() {
    console.log("Hi, I'm " + this.name);
  }
};

console.log(person.name);        // "Alice"
person.greet();                  // "Hi, I'm Alice"
person.job = "Developer";        // Add property
delete person.age;               // Remove property

// Shorthand method
const obj = {
  sayHi() { console.log("Hi!"); }
};
obj.sayHi(); // "Hi!"

// Object destructuring
const { name, job } = person;
```

---

## 9. Functions

### Function Declaration
```js
function add(a, b) {
  return a + b;
}
```

### Function Expression
```js
const multiply = function(a, b) {
  return a * b;
};
```

### Arrow Function (ES6+)
```js
const divide = (a, b) => a / b;
const greet = name => `Hello, ${name}!`; // Single param, no parens needed
```

### Default Parameters
```js
function sayHello(name = "friend") {
  return "Hi, " + name;
}
```

### Rest Parameters & Spread Operator
```js
function sum(...numbers) {
  return numbers.reduce((acc, n) => acc + n, 0);
}
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5]; // [1,2,3,4,5]
```

---

## 10. Control Flow

### If/Else
```js
if (score > 90) {
  console.log("A");
} else if (score > 80) {
  console.log("B");
} else {
  console.log("C or below");
}
```

### Switch
```js
switch (fruit) {
  case "apple":
    // ...
    break;
  case "banana":
    // ...
    break;
  default:
    // ...
}
```

### Loops

- **For Loop:**  
  ```js
  for (let i = 0; i < 5; i++) {
    console.log(i);
  }
  ```
- **While Loop:**  
  ```js
  let i = 0;
  while (i < 5) {
    console.log(i);
    i++;
  }
  ```
- **Do...While Loop:**  
  ```js
  let i = 0;
  do {
    console.log(i);
    i++;
  } while (i < 5);
  ```
- **For...of (arrays):**
  ```js
  for (const fruit of fruits) {
    console.log(fruit);
  }
  ```
- **For...in (objects):**
  ```js
  for (const key in person) {
    console.log(key, person[key]);
  }
  ```
- **Array Methods:**  
  ```js
  fruits.forEach(fruit => console.log(fruit));
  ```

---

## 11. DOM Manipulation (Browser)

### Selecting Elements

```js
const title = document.getElementById("main-title");
const items = document.querySelectorAll(".item"); // NodeList
const firstItem = document.querySelector(".item");
```

### Changing Content and Attributes

```js
title.textContent = "New Title";
title.innerHTML = "<span>New Title</span>";
title.setAttribute("data-type", "main");
```

### Changing Styles

```js
title.style.color = "blue";
title.classList.add("highlight");
title.classList.remove("highlight");
title.classList.toggle("active");
```

### Creating and Removing Elements

```js
const newDiv = document.createElement("div");
newDiv.textContent = "Hello!";
document.body.appendChild(newDiv);

document.body.removeChild(newDiv);
```

---

## 12. Events

### Add an Event Listener

```js
const button = document.querySelector("button");
button.addEventListener("click", function(event) {
  alert("Button clicked!");
});
```
- **Common Events:** `click`, `mouseover`, `mouseout`, `keydown`, `keyup`, `submit`, `change`, `input`
- **Event Object:**  
  ```js
  button.addEventListener("click", (e) => {
    console.log(e.target); // Element that triggered event
  });
  ```

---

## 13. JSON

- **Parse JSON string to JS object:**
  ```js
  const obj = JSON.parse('{"name":"Alice"}');
  ```
- **Stringify JS object to JSON:**
  ```js
  const str = JSON.stringify({ name: "Alice" });
  ```

---

## 14. Fetch API (AJAX Requests)

```js
fetch("https://api.example.com/data")
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error("Fetch error:", error));
```

- **Async/Await (modern syntax):**
  ```js
  async function getData() {
    try {
      const response = await fetch("https://api.example.com/data");
      const data = await response.json();
      console.log(data);
    } catch (error) {
      console.error(error);
    }
  }
  getData();
  ```

---

## 15. ES6+ Features

- **Let/const:** Block-scoped variables.
- **Arrow functions:** Shorter function syntax.
- **Template literals:** `` `Hello, ${name}!` ``
- **Destructuring:** `const {x, y} = point;`
- **Spread/rest:** `const arr2 = [...arr1]`
- **Default params:** `function f(a = 5) {}`
- **Classes:**
  ```js
  class Animal {
    constructor(name) {
      this.name = name;
    }
    speak() {
      console.log(`${this.name} makes a noise.`);
    }
  }
  const dog = new Animal("Dog");
  dog.speak(); // "Dog makes a noise."
  ```
- **Modules (export/import):**
  ```js
  // file1.js
  export const pi = 3.14;

  // file2.js
  import { pi } from './file1.js';
  ```

---

## 16. Error Handling

```js
try {
  // code that might throw
} catch (error) {
  console.error(error);
} finally {
  // always runs
}
```
- **Throwing errors:**  
  ```js
  throw new Error("Something went wrong!");
  ```

---

## 17. Best Practices

- Use `const` and `let` (not `var`)
- Use strict equality (`===`, `!==`)
- Keep code modular and functions small
- Comment code for clarity and maintainability
- Avoid polluting the global namespace
- Test your code in multiple browsers
- Use `async/await` for asynchronous code
- Prefer array methods (`.map`, `.filter`, etc.) over manual loops when possible

---

## 18. Practice Project Ideas

- Build a to-do list app
- Create a calculator
- Make an image slider/gallery
- Fetch and display data from an API
- Build a responsive navigation menu

---

## 19. Further Resources

- [MDN Web Docs: JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [JavaScript.info](https://javascript.info/)
- [Eloquent JavaScript (free book)](https://eloquentjavascript.net/)
- [W3Schools JavaScript Reference](https://www.w3schools.com/js/)
- [You Don’t Know JS (book series)](https://github.com/getify/You-Dont-Know-JS)
---