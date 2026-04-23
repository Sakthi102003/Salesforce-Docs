# LWC Day 3: Data Tables and Component Communication

## Data Management and UI

### Lightning Data Table (`<lightning-datatable>`)
A powerful base component used to display tabular data. It supports features like sorting, row selection, and inline editing.
- **`refreshApex`:** A function used to refresh data provisioned via the wire service without reloading the entire page. This is essential after performing DML operations to ensure the UI stays in sync with the database.

### Toast Messages
Used to provide feedback to users (e.g., success or error notifications) through small, non-intrusive popup messages.

---

## Component Communication
Communication involves passing data between different LWC components.

### 1. Communication Between Related Components
Related components exist in a parent-child hierarchy.

- **Parent to Child Communication:**
  - Data is passed from the outer (parent) component to the inner (child) component.
  - **Tool:** `@api` decorator.
  - By default, JavaScript properties are private. Marking a property with `@api` makes it **public**, allowing a parent component to set its value.

- **Child to Parent Communication:**
  - Data is passed from the inner (child) component up to the outer (parent) component.
  - **Tool:** **Custom Events**.
  - The child dispatches an event, and the parent "listens" for it.
  - **Advanced Event Bubbling:**
    - `bubbles: true`: Allows the event to travel up through the DOM hierarchy to parents and grandparents.
    - `composed: true`: Allows the event to cross the Shadow DOM boundary.

### 2. Communication Between Unrelated Components
For components that do not share a direct parent-child relationship, Salesforce provides the **Lightning Message Service (LMS)**.

#### LMS (Publish-Subscribe Model):
LMS uses a "Message Channel" to facilitate communication across the entire Lightning page.
- **Publisher Component:** Dispatches (publishes) data to a specific message channel.
- **Subscriber Component:** Listens (subscribes) to that message channel to receive and process the data.

---

## Event Types in LWC
- **Standard Events:** Built-in DOM events (e.g., `onclick`, `onchange`, `onfocus`, `onblur`).
- **Custom Events:** Developer-defined events used specifically for component-to-component communication.

---

## Mini Case Study
Introduction to a comprehensive project applying LWC concepts, data tables, and multi-component communication.