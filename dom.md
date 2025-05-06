# DOM Manipulation Cheat Sheet: Beginner to Advanced

> **How to use this guide:**  
> Start from the top for a comprehensive learning curve, or jump to any section for reference. Each topic includes clear explanations, code samples, best practices, and essential tips.

---

## 1. What is the DOM?

**DOM** stands for **Document Object Model**.  
It's a programming interface provided by browsers that represents the structure of HTML and XML documents as a tree of nodes.

- **Nodes** represent elements, text, comments, etc.
- **JavaScript** can traverse, read, and alter any part of the DOM tree.

---

## 2. When to Run DOM Manipulation Code

- Place your JS code **at the end of the `<body>`** so the DOM is loaded.
- Or, run code inside a `DOMContentLoaded` event to ensure the DOM is ready:

```js
document.addEventListener("DOMContentLoaded", function() {
  // DOM manipulation code here
});
```

---

## 3. Selecting Elements

### By ID

```js
const title = document.getElementById("main-title");
```
- Returns the **first element** with the given ID, or `null` if not found.

### By Class Name

```js
const buttons = document.getElementsByClassName("btn");
```
- Returns a **live HTMLCollection** (updates automatically as DOM changes).

### By Tag Name

```js
const paragraphs = document.getElementsByTagName("p");
```
- Returns a **live HTMLCollection**.

### Modern (Recommended): querySelector / querySelectorAll

```js
const firstNav = document.querySelector("nav");             // First <nav>
const allNavLinks = document.querySelectorAll("nav a");     // All <a> in <nav>
const mainSection = document.querySelector("#main-section");// By ID
const items = document.querySelectorAll(".item");           // All elements with class "item"
```
- `querySelector` returns **the first match** (or `null`).
- `querySelectorAll` returns a **static NodeList** (use `.forEach()`).

---

## 4. Reading and Changing Content

### Get/Set Text Content

```js
element.textContent;            // Get text (all text, no HTML)
element.textContent = "Hello";  // Set text (removes HTML)
```

### Get/Set HTML Content

```js
element.innerHTML;                        // Get HTML contents
element.innerHTML = "<strong>Bold!</strong>"; // Set HTML contents
```
**Warning:**  
- Setting `innerHTML` with user input can create security vulnerabilities (XSS).

### Get/Set Value (for Inputs)

```js
input.value = "New value";      // Set input value
let val = input.value;          // Get input value
```

---

## 5. Reading and Changing Attributes

```js
element.getAttribute("href");                   // Get attribute value
element.setAttribute("href", "https://...");    // Set attribute value
element.hasAttribute("data-test");              // true/false
element.removeAttribute("title");               // Remove attribute
```

### Direct Attribute Access

```js
image.src = "cat.jpg";
checkbox.checked = true;
input.placeholder = "Enter your name";
```

---

## 6. Manipulating Classes

```js
element.classList.add("active");        // Add class
element.classList.remove("active");     // Remove class
element.classList.toggle("active");     // Add if missing, remove if present
element.classList.contains("active");   // true/false
```

---

## 7. Changing Styles

```js
element.style.color = "red";
element.style.backgroundColor = "yellow";
element.style.fontSize = "2rem";
```
- Use camelCase for CSS properties: `background-color` → `backgroundColor`.
- For many changes, use a class instead for better maintainability.

---

## 8. Creating, Adding, and Removing Elements

### Create Element

```js
const newDiv = document.createElement("div");
newDiv.textContent = "New content!";
newDiv.classList.add("notice");
```

### Add Element to the DOM

```js
document.body.appendChild(newDiv);                 // Add as last child
parent.insertBefore(newDiv, referenceElement);     // Insert before another element
parent.append(newDiv);                             // (Modern) Append as last child
parent.prepend(newDiv);                            // (Modern) Insert as first child
```

### Remove Element

```js
element.remove();                                  // Modern and preferred
// Or:
parent.removeChild(childElement);                  // Traditional
```

---

## 9. Cloning Elements

```js
const clone = element.cloneNode(true); // true = deep clone (with children)
document.body.appendChild(clone);
```

---

## 10. Traversing the DOM

```js
element.parentNode;               // Parent node (may be an element or document)
element.parentElement;            // Parent element (null if not an element)
element.children;                 // HTMLCollection of child elements
element.childNodes;               // NodeList (includes text/comments)
element.firstElementChild;        // First child element
element.lastElementChild;         // Last child element
element.previousElementSibling;   // Previous sibling element
element.nextElementSibling;       // Next sibling element
```

---

## 11. Handling Events

### Add an Event Listener

```js
element.addEventListener("click", function(event) {
  alert("Element clicked!");
});
```

- **Common Events:** `click`, `dblclick`, `mouseover`, `mouseout`, `mousedown`, `mouseup`, `keydown`, `keyup`, `submit`, `input`, `change`, `focus`, `blur`
- **Arrow functions** can be used, but `function()` has its own `this` (sometimes needed).

### Remove an Event Listener

```js
function handleClick() { alert("Clicked!"); }
element.addEventListener("click", handleClick);
// Later:
element.removeEventListener("click", handleClick);
```

### Event Object

```js
element.addEventListener("click", function(event) {
  console.log(event.target); // Element that triggered the event
  event.preventDefault();    // Prevent default action (e.g., form submission)
  event.stopPropagation();   // Stop event from bubbling up
});
```

---

## 12. Event Delegation (Bubbling)

- Attach one event listener to a parent for all current and **future** child elements.

```js
list.addEventListener("click", function(event) {
  if (event.target.matches(".remove-btn")) {
    event.target.parentElement.remove();
  }
});
```
**Why use delegation?**  
- More efficient for dynamic lists, fewer handlers, works for elements added later.

---

## 13. Modifying Forms

```js
const form = document.querySelector("form");
form.addEventListener("submit", function(event) {
  event.preventDefault(); // Stop page reload
  const name = form.elements["username"].value;
  alert("Submitted: " + name);
});
```

- Use `.elements["fieldname"]` to get form fields by name.
- Use `input.value` to read/set field values.

---

## 14. Working with Data Attributes

- **HTML:**  
  ```html
  <div data-user-id="42"></div>
  ```
- **JavaScript:**  
  ```js
  const div = document.querySelector("div");
  let id = div.dataset.userId;       // "42"
  div.dataset.role = "admin";        // Set new data attribute
  ```

---

## 15. Animating the DOM

- **Best practice:** Use CSS transitions/animations and toggle classes with JS.

```js
element.classList.add("fade-in");
```
```css
.fade-in {
  opacity: 1;
  transition: opacity 0.5s;
}
```

- For advanced, use the [Web Animations API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Animations_API).

---

## 16. Performance Tips

- **Minimize DOM updates:** Batch changes where possible.
- **Use classes instead of direct styles** for multiple changes.
- **Avoid excessive querying** (cache references to frequently-used elements).
- **Detach elements** before making many changes, then re-attach.

---

## 17. Accessibility Considerations

- **Update ARIA attributes** as needed (e.g., `aria-expanded` for menus).
- **Use focus management** (`element.focus()`) for modals/popups.
- **Announce changes** with ARIA live regions when content updates dynamically.

---

## 18. Practice Project Ideas

- Toggle dark/light mode by adding/removing a class on the `<body>`.
- Build a to-do list where clicking an item removes it.
- Create an expandable/collapsible FAQ section.
- Build a modal popup that opens/closes with a button.
- Create a live character counter for a text input.

---

## 19. Further Resources

- [MDN Web Docs: DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)
- [MDN Web Docs: Introduction to the DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
- [JavaScript Event Reference](https://developer.mozilla.org/en-US/docs/Web/Events)