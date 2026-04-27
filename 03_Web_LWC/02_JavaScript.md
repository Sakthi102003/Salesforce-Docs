# JavaScript Fundamentals

## Introduction
JavaScript is an object-oriented scripting language used to add logic and interactivity to web pages. While HTML provides structure and CSS provides styling, JavaScript handles the behavior.

### Client-Side Scripting
In a **Client-Server Architecture**, JavaScript allows us to handle user interactions and events directly in the browser (client side). This reduces the number of requests sent to the server, resulting in a faster and smoother user experience.

---

## Variables in JavaScript
JavaScript is dynamically typed, meaning you do not need to explicitly define data types. Types are determined at runtime.

### Declaration Keywords:
1. **`var`:**
   - **Scope:** Function-scoped.
   - **Behavior:** Allows both re-declaration and re-assignment. If declared outside a function, it becomes global.
   ```javascript
   var num = 100;
   var num = 200; // Allowed
   ```
2. **`let`:**
   - **Scope:** Block-scoped (e.g., inside an `if` statement or a `loop`).
   - **Behavior:** Allows re-assignment but **prohibits** re-declaration within the same scope.
   ```javascript
   let a = 'Salesforce';
   a = 'Apex'; // Allowed
   // let a = 500; // Error: Identifier 'a' has already been declared
   ```
3. **`const`:**
   - **Scope:** Block-scoped.
   - **Behavior:** Used for constants. It requires initialization upon declaration and **prohibits** both re-declaration and re-assignment.
   ```javascript
   const pi = 3.14;
   // pi = 3.15; // Error: Assignment to constant variable
   ```

---

## Functions
Functions are reusable blocks of code.

### 1. Pre-defined Functions:
- **`setTimeout(function, delay)`:** Executes a function once after a specified delay (in milliseconds).
- **`setInterval(function, interval)`:** Executes a function repeatedly at specified intervals.
- **`isNaN(value)`:** Returns `true` if the value is "Not-a-Number," and `false` if it is a valid number.

### 2. Specialized Functions:
- **User-Defined Functions:** Custom functions created by the developer.
- **Callback Functions:** A function passed as an argument to another function, to be executed later.

---

## Document Object Model (DOM)
The DOM is a programming interface that represents an HTML document as a tree structure. JavaScript uses the `document` object to interact with and manipulate the page content.

### Common DOM Methods:
- `document.write()`: Writes directly to the HTML output stream.
- `document.getElementById('id')`: Returns the element with the specified ID.
- `document.getElementsByClassName('class')`: Returns a collection of elements with the specified class name.
- `document.getElementsByTagName('tag')`: Returns a collection of elements with the specified tag name.
- `document.getElementsByName('name')`: Returns a collection of elements with the specified name attribute.