
# HTML Cheat Sheet: From Beginner to Advanced

> **How to use this guide:**  
> Start at the top for a step-by-step foundation, or jump to any section for reference. Each topic includes explanations, code examples, and best practices.

---

## 1. Getting Started with HTML

### What is HTML?
HTML (HyperText Markup Language) is the standard language for creating web pages. It structures content with elements called “tags.”

### Basic Document Structure
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Your Page Title</title>
  </head>
  <body>
    <!-- Page content goes here -->
  </body>
</html>
```
- `<!DOCTYPE html>`: Declares the document type.
- `<html>`: Root element.
- `<head>`: Metadata (not displayed).
- `<body>`: Page content.

---

## 2. Common Elements & What They Do

| Tag            | Purpose                                       | Example                            |
|----------------|-----------------------------------------------|------------------------------------|
| `<h1>`-`<h6>`  | Headings (1=most important)                   | `<h1>Hello</h1>`                   |
| `<p>`          | Paragraph                                     | `<p>This is text.</p>`             |
| `<a>`          | Link to another page or URL                   | `<a href="https://...">Link</a>`   |
| `<img>`        | Displays an image                             | `<img src="img.jpg" alt="Desc">`   |
| `<ul>` / `<ol>`| Unordered/Ordered list                        | `<ul><li>Item</li></ul>`           |
| `<li>`         | List item (inside `<ul>` or `<ol>`)           | `<li>Item</li>`                    |
| `<div>`        | Block-level container for content             | `<div>Section</div>`               |
| `<span>`       | Inline container for text                     | `<span>Highlight</span>`           |
| `<strong>`     | Important (bold) text                         | `<strong>Warning!</strong>`        |
| `<em>`         | Emphasized (italic) text                      | `<em>Note</em>`                    |
| `<br>`         | Line break                                    | `First<br>Second`                  |
| `<hr>`         | Horizontal line                               | `<hr>`                             |

---

## 3. Attributes

- Add extra information to elements.
- **Format:** `attribute="value"`

**Common Attributes:**
- `id`, `class`
- `href` (for `<a>`)
- `src`, `alt` (for `<img>`)
- `style`
- `title`
- `target` (e.g., `target="_blank"` for new tab)

**Example:**
```html
<a href="https://example.com" target="_blank" title="Visit Example">Visit</a>
<img src="cat.jpg" alt="A cute cat" />
```

---

## 4. Semantic HTML

Use elements that describe their meaning for better accessibility and SEO.

| Tag           | Purpose                         |
|---------------|---------------------------------|
| `<header>`    | Page or section header          |
| `<nav>`       | Navigation links                |
| `<main>`      | Main site content               |
| `<article>`   | Independent content (e.g., post)|
| `<section>`   | Thematic grouping of content    |
| `<aside>`     | Side content (sidebar, ads)     |
| `<footer>`    | Footer for page or section      |
| `<figure>`    | Image or illustration group     |
| `<figcaption>`| Caption for a figure            |

**Example:**
```html
<main>
  <article>
    <header><h1>Article Title</h1></header>
    <p>Content...</p>
    <footer>Written by Author</footer>
  </article>
</main>
```

---

## 5. Forms

For user input and interaction.

**Basic Structure:**
```html
<form action="/submit" method="POST">
  <label for="name">Name:</label>
  <input type="text" id="name" name="name" required />

  <label for="email">Email:</label>
  <input type="email" id="email" name="email" />

  <input type="submit" value="Send" />
</form>
```

**Common Input Types:**  
`text`, `password`, `email`, `number`, `checkbox`, `radio`, `file`, `submit`, `button`, `date`, `range`

---

## 6. Tables

To display structured/tabular data.

```html
<table>
  <caption>Sample Table</caption>
  <thead>
    <tr>
      <th>Name</th><th>Age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Alice</td><td>22</td>
    </tr>
  </tbody>
</table>
```
- `<table>`: Table container
- `<tr>`: Table row
- `<th>`: Table header cell
- `<td>`: Table data cell
- `<thead>`, `<tbody>`, `<tfoot>`: Table sections

---

## 7. Embedding Media

- **Images:**  
  `<img src="..." alt="Description">`
- **Audio:**  
  `<audio controls src="sound.mp3"></audio>`
- **Video:**  
  `<video controls width="320" src="movie.mp4"></video>`
- **YouTube:**  
  `<iframe width="560" height="315" src="https://www.youtube.com/embed/ID"></iframe>`

---

## 8. Linking CSS & JavaScript

- **CSS (in `<head>`):**
  ```html
  <link rel="stylesheet" href="styles.css" />
  ```
- **JavaScript (before `</body>`):**
  ```html
  <script src="script.js"></script>
  ```

---

## 9. Comments

```html
<!-- This is a comment -->
```

---

## 10. Accessibility Best Practices

- Use semantic elements (`<nav>`, `<main>`, etc.)
- Always provide `alt` for images.
- Use `<label>` for form inputs.
- Ensure sufficient color contrast (in CSS).
- Use headings in order (`<h1>` before `<h2>`, etc.).
- Don’t rely on color alone to convey meaning.

---

## 11. SEO Best Practices

- Use descriptive `<title>` and `<meta name="description">` in `<head>`.
- Use semantic tags.
- Use heading tags for structure.
- Use `alt` text on images.

---

## 12. Advanced: Meta Tags

- **Charset:**  
  `<meta charset="UTF-8">`
- **Viewport (responsive):**  
  `<meta name="viewport" content="width=device-width, initial-scale=1">`
- **Description (SEO):**  
  `<meta name="description" content="Description of page">`

---

## 13. Practice Project Ideas

- Build a personal portfolio page.
- Make a blog post template.
- Create a contact form.
- Build a product table.
- Make a photo gallery with captions.

---

## 14. Further Resources

- [MDN Web Docs: HTML](https://developer.mozilla.org/en-US/docs/Web/HTML)
- [W3Schools HTML Reference](https://www.w3schools.com/tags/)
- [HTML5 Doctor – Semantic Elements](http://html5doctor.com/element-index/)
- [WebAIM – Accessibility](https://webaim.org/techniques/)

---

**Would you like this as a ready-to-copy Markdown file (`html-cheatsheet.md`)? If yes, I can provide the Markdown source for you to create the file in your repo, or guide you step-by-step as I did before. Let me know how you want to proceed!**