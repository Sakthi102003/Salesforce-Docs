# LWC Day 2: Apex Integration and Modern JavaScript

## Modern JavaScript Features

### Callback Functions
A callback is a function passed as an argument to another function. This allows for asynchronous behavior, where a function waits for another process to complete before executing.

### Arrow Functions (`=>`)
Arrow functions provide a more concise syntax for writing function expressions.
- **Advantages:**
  - Easier to read and write.
  - Lexical `this` binding: Unlike regular functions, arrow functions do not have their own `this` context, making them ideal for LWC handlers.
  ```javascript
  (data) => {
      console.log('Received data:', data);
  }
  ```

---

## Integrating Apex with LWC
To display Salesforce data in an LWC, you must use an Apex class. The Apex method must be annotated with `@AuraEnabled(cacheable=true)` to be used with the wire service.

### 1. The `@wire` Service
The wire service is reactive; it automatically refreshes the data when the underlying records change.
- **@wire with Property:** Fetches data and stores it directly in a JavaScript property.
  - *Best for:* Simple data display.
- **@wire with Function:** Fetches data and passes it to a function (taking an object with `data` and `error` as parameters).
  - *Best for:* Performing logic or data transformation before displaying.

### 2. Imperative Approach
Imperative calling allows you to invoke an Apex method in response to a specific user action (e.g., clicking a button).
- **Scenario:** A page with three buttons:
  - "All Opportunities"
  - "Won Opportunities"
  - "Lost Opportunities"
- Each button click triggers a specific call to Apex to fetch the filtered list.

---

## LWC Component Lifecycle Hooks
Lifecycle hooks are specialized methods that execute at specific stages of a component's existence:

1. **`constructor()`:** Invoked when the component instance is first created. Used for initialization but cannot access the DOM or component attributes.
2. **`connectedCallback()`:** Invoked when the component is inserted into the Document Object Model (DOM). Ideal for fetching initial data.
3. **`renderedCallback()`:** Invoked after every render of the component. Use with caution to avoid infinite loops.
4. **`errorCallback(error, stack)`:** Invoked when a descendant component throws an error.
5. **`disconnectedCallback()`:** Invoked when the component is removed from the DOM. Used for cleanup (e.g., clearing timers).

---

## Data Handling in LWC
When receiving data from an Apex method (especially via `@wire`), the result is typically an object containing:
- **`data`:** The successful payload from the server.
- **`error`:** Information about any failure that occurred during the request.