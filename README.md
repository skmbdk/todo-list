# Vanilla JS Task Manager (DOM + Events + Rendering Pipeline)

This project is a single-page Vanilla JavaScript **Task Manager** UI stored in:
- `projects/todo list/app.html`

It demonstrates:
- DOM creation and updates (task cards)
- LocalStorage persistence
- **Event Bubbling + Event Capturing**
- **Event Delegation**
- **Browser Rendering Pipeline** concepts (HTML → DOM → CSSOM → Render Tree)
- Pagination and filtering

---

## Browser Rendering Pipeline (Concepts)
When the page loads, the browser follows these high-level steps:

### 1) Parsing (HTML Parsing)
The browser reads your HTML markup and parses it into tokens and structures.

### 2) Tokenization
HTML is broken down into tokens (tags, attributes, text nodes, etc.).

### 3) DOM Tree
Tokens are organized into the **DOM Tree** (Document Object Model). This is a structured representation of the HTML.

### 4) CSSOM Tree
In parallel, the browser parses CSS and builds the **CSSOM Tree** (CSS Object Model), representing styles and rules.

### 5) Render Tree
The browser combines:
- the **DOM Tree**
- the **CSSOM Tree**

…to create the **Render Tree**, which represents exactly what will be shown on screen (after styles are resolved and non-visible nodes are filtered).

---

## Event Bubbling
**Bubbling** is the default event flow:
- event target → parent → grandparent → …

In this app, the “Bubbling Example” buttons demonstrate that clicking the child triggers listeners up the DOM.

---

## Event Capturing
**Capturing** is the opposite flow:
- document/grandparent → … → parent → event target

In this app, the “Capturing Example” uses `addEventListener(..., true)` to run handlers during the capturing phase.

---

## Event Delegation
Instead of attaching click handlers to every dynamically created task button, the app uses **one listener** on the container:
- `taskContainer.addEventListener('click', ...)`

Then it detects which button was clicked using:
- `event.target.closest('button')`
- and reads `data-action` / `data-id`

This makes the code work efficiently even as tasks are added/removed.

---

## Task Features
- Add Task (title + category)
- Edit / Complete (toggle) / Delete
- Clear Completed / Clear All
- Search + category filter
- Pagination (5 tasks per page)
- Theme toggle (light/dark) with a click animation

---

## Files
- **Main page**: `projects/todo list/app.html`
- **No build step** required (pure HTML/CSS/JS in the file).

