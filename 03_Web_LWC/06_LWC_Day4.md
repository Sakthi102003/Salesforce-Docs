# LWC Day 4: Advanced Features and Case Study

## Mini Case Study Architecture
The case study involves a modular architecture with six interacting Lightning Web Components.

### Component Relationship:
1. **`caseStudyLayout`:** The master container (parent) for the application.
2. **`caseStudyNavigation`:** A vertical navigation child component.
3. **`accountSearchResult`:** Displays a list of accounts based on search criteria.
   - **Role:** Publisher (via LMS).
   - **Child:** `accountSearchInput`: The input field used to filter results.
4. **`accountDetail`:** Displays detailed information for a selected account.
   - **Role:** Subscriber (via LMS).
   - **Child:** `accountMap`: Uses Salesforce Maps to display the account's physical location.

---

## Lightning Data Service (LDS)
LDS allows you to perform basic CRUD operations (Create, Read, Update, Delete) on a single record without writing any Apex code or SOQL queries.

- **Available Tools:** `<lightning-record-view-form>`, `<lightning-record-edit-form>`, and `<lightning-record-form>`.
- **Limitation:** LDS is optimized for **single-record operations**. For bulk data or complex filtering, an Apex class is required.
- **Example:** Using `record-view-form` to display `Account Name`, `Type`, and `Industry` directly on the page.

---

## Specialized LWC Features

### NavigationMixin
The `NavigationMixin` is used to navigate from an LWC to various targets within Salesforce, such as:
- A specific **Record Page**.
- A standard or custom **App Page**.
- The **Home Page**.
- An external URL.

### Service / Utility Components
A **Service Component** is a component that contains only logic (in the `.js` file) and has an empty template (`.html`).
- **Purpose:** Acts as a library of reusable functions and calculations that can be imported and used by multiple other components across the organization.

### Custom Data Attributes
Used to store extra information on standard or custom HTML elements.
- **Syntax:** `data-*` (e.g., `<lightning-input data-id="uniqueId">`).
- **Usage:** In JavaScript, these attributes are accessed via `event.target.dataset.id`.

### Billing Address Component
A specialized input component used to collect structured address data, including:
- Street
- City
- State/Province
- Country
- Postal Code (Zip Code)