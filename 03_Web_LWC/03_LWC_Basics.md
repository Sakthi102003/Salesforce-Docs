# Lightning Web Components (LWC) Basics

## Introduction to Lightning Components
Salesforce has evolved from a page-centric model to a component-centric architecture.

- **Salesforce Classic (Visualforce):** Uses a traditional, single-page approach to web development.
- **Salesforce Lightning (Aura & LWC):** Built on a modern component framework where a page is a collection of reusable, independent components.

---

## LWC Component Bundle
An LWC component consists of several files working together:
- **`.html`:** Defines the structure (template) of the component.
- **`.js`:** Handles the logic and data management.
- **`.js-meta.xml`:** Metadata file that defines where the component can be used (e.g., Record Page, Home Page).
- **`.css` (Optional):** Provides custom styling for the component.
- **`.svg` (Optional):** Used for custom icons.

---

## Development Workflow with Salesforce DX
Salesforce Developer Experience (SFDX) provides the tools needed for modern development in VS Code.

### Steps to Create and Deploy a Project:
1. **Initialize Folder:** Create a local folder for your project.
2. **Open in VS Code:** Launch VS Code within that folder.
3. **Create Project:** Run the `SFDX: Create Project` command.
4. **Authorize Org:** Connect to your Salesforce environment using `SFDX: Authorize an Org`.
5. **Create Component:** Run `SFDX: Create Lightning Web Component` to generate the bundle.
6. **Deploy:** Use `SFDX: Deploy Source to Org` to push your changes to Salesforce.

---

## Targeted Lightning Pages
For a component to be visible, it must be exposed to one or more of these page types:
1. **Record Page:** Displays details for a specific object record (e.g., a specific Account).
2. **App Page:** A custom page created for a specific application.
3. **Home Page:** The default landing page for users.

---

## Core LWC Concepts

### DOM Event Handlers
Events are user interactions like clicks or input changes.
- **Events:** `onclick`, `onchange`, `onfocus`, `onblur`.
- **Event Handler:** A JavaScript function (e.g., `handleClick()`) that executes in response to an event.

### Base Lightning Components
Salesforce provides high-level components with built-in styling and accessibility:
- `<lightning-card>`: A container for grouping related information.
- `<lightning-button>`: A standard button component.
- `<lightning-input>`: Used to collect various types of user input.
- `<lightning-combobox>`: A picklist or dropdown component.

---

## Styling and Design
1. **Salesforce Lightning Design System (SLDS):** A comprehensive design framework provided by Salesforce to ensure components look native.
   - Documentation: [lightningdesignsystem.com](https://v1.lightningdesignsystem.com/)
2. **Custom CSS:** Developers can define their own styles in the `.css` file for unique branding needs.