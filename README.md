# Salesforce Technical Documentation Hub

Welcome to the **Salesforce Technical Documentation Hub**. This repository contains a structured and comprehensive set of notes, guides, and best practices for Salesforce development and administration, organized in a sequential learning path.

---

## 📁 Folder Structure

```text
clean_salesforce_md/
├── 01_Admin/                # Core Admin, Security, and Flows
├── 02_Development/          # Apex, SOQL, Testing, and Integration
├── 03_Web_LWC/              # HTML/CSS, JS, and Lightning Web Components
└── README.md                # Project Index
```

---

## 📚 Table of Contents

### 1. Salesforce Fundamentals & Administration
*   **[01. SFDC Introduction](01_Admin/01_SFDC_Intro.md):** Cloud computing basics, CRM core concepts, and the Salesforce multi-tenant architecture.
*   **[02. Object Relationships](01_Admin/02_Relationships.md):** Mastering Lookup, Master-Detail, and Junction Objects for effective data modeling.
*   **[03. Security & Identity](01_Admin/03_Security.md):** Deep dive into the Salesforce security model, from Profiles and Permission Sets to the "Sharing Waterfall."
*   **[04. Validation & Security](01_Admin/04_Validation_Security.md):** Best practices for data integrity using Validation Rules and field-level security.
*   **[05. Salesforce Flows](01_Admin/05_Flows.md):** Declarative automation including Record-Triggered and Screen Flows.
*   **[06. Reports & Dashboards](01_Admin/06_Reports_Data.md):** Leveraging analytics and managing data import/export processes.

### 2. Programmatic Development (Apex)
*   **[01. Apex Basics](02_Development/01_Apex_Basics.md):** Introduction to Apex syntax, collections (List, Set, Map), and object-oriented programming.
*   **[02. SOQL (Salesforce Object Query Language)](02_Development/02_SOQL.md):** Detailed guide on querying data and handling relationship queries.
*   **[03. SOSL & DML](02_Development/03_SOSL_DML.md):** Comprehensive search techniques and data manipulation operations.
*   **[04. Apex Triggers](02_Development/04_Apex_Triggers.md):** Mastering trigger context variables, bulkification, and event handling.
*   **[05. Apex Testing](02_Development/05_Apex_Testing.md):** Ensuring code quality through unit tests, mock data, and high code coverage.
*   **[06. Asynchronous Apex](02_Development/06_Async_Apex.md):** Scaling applications with Future methods, Batch Apex, and Queueable jobs.
*   **[07. Integration](02_Development/07_Integration.md):** Connecting Salesforce with external systems using REST/SOAP APIs and the Software Development Life Cycle (SDLC).

### 3. Modern Web Development & LWC
*   **[01. HTML & CSS](03_Web_LWC/01_HTML_CSS.md):** Fundamentals of web structure and styling tailored for Salesforce developers.
*   **[02. JavaScript Fundamentals](03_Web_LWC/02_JavaScript.md):** ES6+ features, DOM manipulation, and asynchronous programming.
*   **[03. Lightning Web Components (LWC) Basics](03_Web_LWC/03_LWC_Basics.md):** Introduction to the LWC component bundle and local development setup.
*   **[04. LWC Advanced - Day 2](03_Web_LWC/04_LWC_Day2.md):** Integrating Apex with LWC via the `@wire` service and imperative calls.
*   **[05. LWC Communication - Day 3](03_Web_LWC/05_LWC_Day3.md):** Parent-Child communication, Custom Events, and Lightning Message Service (LMS).
*   **[06. LWC Specialized Features - Day 4](03_Web_LWC/06_LWC_Day4.md):** Advanced LDS (Lightning Data Service), NavigationMixin, and reusable Multi-component Case Studies.

---

## 🚀 How to Use This Documentation
The files are numbered to guide you through a logical learning path. It is recommended to follow the sequence from **01_Admin** through **03_Web_LWC**.

*   **For Admins:** Start with [01. SFDC Introduction](01_Admin/01_SFDC_Intro.md) and progress through the numbered files in `01_Admin`.
*   **For Developers:** After mastering the Admin essentials, dive into [01. Apex Basics](02_Development/01_Apex_Basics.md) and the [LWC Series](03_Web_LWC/03_LWC_Basics.md).

---

*Documentation maintained for professional Salesforce learning and reference.*

