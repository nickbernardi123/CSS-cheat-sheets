# JavaScript Libraries & React Cheat Sheet (with Alternatives)

> **How to use this guide:**  
> Start from the top for a thorough foundation, or jump to any section for reference. Every section contains clear explanations, best practices, and actionable steps.  
> **React** is the main focus, but you’ll also find guidance on picking and trying other libraries.

---

## 1. What is a JavaScript Library?

- A **library** is a collection of pre-written code that makes development faster and easier.
- You use a library by “calling” its functions/components when you need them.
- **React** is a library for building user interfaces. It helps you create web apps out of reusable components.
- **Difference:**  
  - **Library:** You control the flow, and you choose when/how to use it (e.g. React, Lodash, Axios, Chart.js).
  - **Framework:** The framework controls the flow and tells you where your code fits in (e.g. Angular, Next.js, Vue CLI).

---

## 2. Why Use a Library Like React?

- **Reusable Components:** Break UI into pieces you can reuse and test.
- **Declarative:** Write what the UI should look like for any given state.
- **Efficient DOM Updates:** React efficiently updates only the parts of the UI that change.
- **Large Ecosystem:** Many packages, tools, and tutorials are available.
- **Good for SPAs:** Makes building single-page applications easier and more maintainable.

---

## 3. How to Find and Evaluate JavaScript Libraries

### A. Discovering Libraries

1. **NPM (Node Package Manager)**
   - [npmjs.com](https://www.npmjs.com/) is the main registry for JavaScript libraries.
   - Search for keywords related to your needs (e.g. “UI”, “form validation”, “charts”).

2. **GitHub**
   - Search for libraries by topic, stars, and activity.
   - Check if the repo is actively maintained.

3. **Awesome Lists**
   - Community-curated lists of great libraries (e.g. [awesome-react](https://github.com/enaqx/awesome-react), [awesome-javascript](https://github.com/sorrycc/awesome-javascript)).

4. **Google and Blogs**
   - Search for “best JavaScript libraries for X”, and read comparisons.

### B. How to Evaluate a Library

- **Popularity:** Is it widely used? (NPM downloads, GitHub stars)
- **Maintenance:** Is it actively maintained and updated?
- **Documentation:** Is the documentation clear and thorough?
- **Community:** Active issues, Stack Overflow questions, Discord/Slack/Reddit communities.
- **Compatibility:** Does it work with your tech stack (React, Vue, TypeScript, etc.)?
- **License:** Most libraries are MIT or open source, but always check.

---

## 4. Setting Up a React Project

### A. Using Vite (Fastest, Recommended)

```bash
npm create vite@latest my-react-app -- --template react
cd my-react-app
npm install
npm run dev
```

### B. Using Create React App (Still Common)

```bash
npx create-react-app my-react-app
cd my-react-app
npm start
```

### C. Basic Project Structure

```
my-react-app/
  ├─ public/
  ├─ src/
  │   ├─ App.jsx
  │   ├─ main.jsx (or index.js)
  │   └─ components/
  ├─ package.json
  └─ ...
```

---

## 5. React Fundamentals

### A. JSX (JavaScript + XML)

- Allows you to write HTML-like syntax in JS files.
- Example:
  ```jsx
  <h1>Hello, {name}!</h1>
  ```

### B. Components

- Small, reusable pieces of UI.
- **Function Component Example:**
  ```jsx
  function Welcome(props) {
    return <h2>Hello, {props.name}!</h2>;
  }
  ```
- **Using a Component:**
  ```jsx
  <Welcome name="Alice" />
  ```

### C. Props (Passing Data)

- Props are arguments passed to components.
  ```jsx
  function Greeting({ name }) {
    return <p>Hi, {name}</p>;
  }
  <Greeting name="Bob" />
  ```

### D. State

- State is data that changes over time and causes the UI to update.
  ```jsx
  import { useState } from 'react';
  function Counter() {
    const [count, setCount] = useState(0);
    return (
      <button onClick={() => setCount(count + 1)}>
        Count: {count}
      </button>
    );
  }
  ```

### E. Events

- Use camelCase event names (onClick, onChange).
  ```jsx
  <button onClick={() => alert('Clicked!')}>Click me</button>
  ```

---

## 6. Lists, Keys, and Conditional Rendering

### A. Lists & Keys

```jsx
const items = ['apple', 'banana', 'orange'];
<ul>
  {items.map((item, idx) => <li key={idx}>{item}</li>)}
</ul>
```
- Always use a unique `key` prop.

### B. Conditional Rendering

```jsx
{isLoggedIn ? <p>Welcome!</p> : <p>Please log in.</p>}
```

---

## 7. Forms and Controlled Inputs

```jsx
import { useState } from 'react';

function MyForm() {
  const [text, setText] = useState('');
  function handleChange(e) {
    setText(e.target.value);
  }
  function handleSubmit(e) {
    e.preventDefault();
    alert(text);
  }
  return (
    <form onSubmit={handleSubmit}>
      <input value={text} onChange={handleChange} />
      <button type="submit">Submit</button>
    </form>
  );
}
```

---

## 8. Side Effects (useEffect)

```jsx
import { useState, useEffect } from 'react';

function DataFetcher() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(res => res.json())
      .then(setData);
  }, []); // Runs once on mount

  return <div>{data ? JSON.stringify(data) : "Loading..."}</div>;
}
```

---

## 9. Styling in React

### A. CSS Files (Recommended)

```jsx
import './App.css';
<div className="my-class">Styled!</div>
```

### B. Inline Styles

```jsx
<div style={{ color: 'red', fontWeight: 'bold' }}>Red Bold</div>
```

### C. CSS-in-JS Libraries

- [styled-components](https://styled-components.com/)
- [emotion](https://emotion.sh/docs/introduction)
- [Tailwind CSS](https://tailwindcss.com/) (utility-first CSS framework)

---

## 10. Organizing Larger React Apps

- Use a `/components` directory for reusable UI pieces.
- Split complex code into smaller, focused components.
- Use hooks for shared logic (e.g., `useEffect`, `useState`).

---

## 11. Importing and Using Other Libraries in React

- Install via NPM:
  ```bash
  npm install axios
  ```
- Import where needed:
  ```jsx
  import axios from 'axios';
  ```

- Example: Fetching with Axios
  ```jsx
  useEffect(() => {
    axios.get('https://api.example.com/data')
      .then(res => setData(res.data));
  }, []);
  ```

---

## 12. Common Pitfalls in React

- Don’t mutate state directly (use the setter function).
- Each list item must have a unique `key`.
- Always close JSX tags (`<img />` not `<img>`).
- Do not call event handler functions directly in JSX (`onClick={handleClick}` not `onClick={handleClick()}`).

---

## 13. How to Find and Try Other UI Libraries

### A. Popular Alternatives

| Name         | Type       | Use Case                                     | Docs                        |
|--------------|------------|----------------------------------------------|-----------------------------|
| **Vue.js**   | Framework  | Easy syntax, learning curve similar to React | [vuejs.org](https://vuejs.org/) |
| **Svelte**   | Compiler   | Simple, fast, no virtual DOM                 | [svelte.dev](https://svelte.dev/) |
| **Angular**  | Framework  | Full-featured, enterprise apps, TypeScript   | [angular.io](https://angular.io/) |
| **Preact**   | Library    | Lightweight React alternative                | [preactjs.com](https://preactjs.com/) |
| **Lit**      | Library    | Web components, modern, fast                 | [lit.dev](https://lit.dev/) |

### B. How to Try an Alternative

1. **Find the official website and documentation.**
   - Example: [https://vuejs.org/guide/introduction.html](https://vuejs.org/guide/introduction.html)
2. **Install using NPM (check the docs for the command).**
   - Example: `npm install vue`
3. **Follow the “Getting Started” guide in the docs.**
4. **Build a small project or component to test it out.**
5. **Compare:**
   - Syntax (is it easy to understand?)
   - Community support (are there tutorials, Stack Overflow answers?)
   - Ecosystem (does it have the features you need?)

### C. How to Search for New Libraries

- Use [npmjs.com](https://www.npmjs.com/) and search for your need (“table”, “datepicker”, “state management”).
- Look up “best JavaScript libraries for [your need]” on Google.
- Check out [Awesome JavaScript](https://github.com/sorrycc/awesome-javascript) and [Awesome React](https://github.com/enaqx/awesome-react) lists on GitHub.

---

## 14. Best Practices for Using Any UI Library

- Start small: Build a simple component before committing to a library.
- Read the documentation and official guides.
- Use the latest stable versions.
- Prefer libraries with active maintenance and large communities.
- Keep your dependencies up to date.
- Use version control (Git) for every project.

---

## 15. Practice Project Ideas

- Build a to-do list app (add, edit, delete items).
- Create a weather dashboard using a public API.
- Make a calculator with React, Vue, or Svelte.
- Build a responsive photo gallery.
- Try re-building the same small app in React, Vue, and Svelte to see differences.

---

## 16. Further Resources

- [React Official Documentation](https://react.dev/)
- [Vue.js Official Docs](https://vuejs.org/guide/introduction.html)
- [Svelte Tutorial](https://svelte.dev/tutorial/basics)
- [Angular Getting Started](https://angular.io/start)
- [Awesome JavaScript](https://github.com/sorrycc/awesome-javascript)
- [Awesome React](https://github.com/enaqx/awesome-react)
- [npmjs.com](https://www.npmjs.com/)

---