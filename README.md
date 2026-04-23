# Salesforce Technical Documentation Hub

Welcome to the **Salesforce Technical Documentation Hub**. This repository contains a structured and comprehensive set of notes, guides, and best practices for Salesforce development and administration.

---

## 📁 Folder Structure

```text
clean_salesforce_md/
├── Admin/                   # Core Admin, Security, and Flows
├── Development/             # Apex, SOQL, Testing, and Integration
├── Web_LWC/                 # HTML/CSS, JS, and Lightning Web Components
└── README.md                # Project Index
```

---


## 📚 Table of Contents

### 1. Salesforce Fundamentals & Administration
*   **[SFDC Introduction](Admin/SFDC_Intro.md):** Cloud computing basics, CRM core concepts, and the Salesforce multi-tenant architecture.
*   **[Object Relationships](Admin/Relationships.md):** Mastering Lookup, Master-Detail, and Junction Objects for effective data modeling.
*   **[Security & Identity](Admin/Security.md):** Deep dive into the Salesforce security model, from Profiles and Permission Sets to the "Sharing Waterfall."
*   **[Validation & Security](Admin/Validation_Security.md):** Best practices for data integrity using Validation Rules and field-level security.
*   **[Reports & Dashboards](Admin/Reports_Data.md):** Leveraging analytics and managing data import/export processes.
*   **[Salesforce Flows](Admin/Flows.md):** Declarative automation including Record-Triggered and Screen Flows.

### 2. Programmatic Development (Apex)
*   **[Apex Basics](Development/Apex_Basics.md):** Introduction to Apex syntax, collections (List, Set, Map), and object-oriented programming.
*   **[SOQL (Salesforce Object Query Language)](Development/SOQL.md):** Detailed guide on querying data and handling relationship queries.
*   **[SOSL & DML](Development/SOSL_DML.md):** Comprehensive search techniques and data manipulation operations.
*   **[Apex Triggers](Development/Apex_Triggers.md):** Mastering trigger context variables, bulkification, and event handling.
*   **[Asynchronous Apex](Development/Async_Apex.md):** Scaling applications with Future methods, Batch Apex, and Queueable jobs.
*   **[Apex Testing](Development/Apex_Testing.md):** Ensuring code quality through unit tests, mock data, and high code coverage.
*   **[Integration](Development/Integration.md):** Connecting Salesforce with external systems using REST/SOAP APIs and the Software Development Life Cycle (SDLC).

### 3. Modern Web Development & LWC
*   **[HTML & CSS](Web_LWC/HTML_CSS.md):** Fundamentals of web structure and styling tailored for Salesforce developers.
*   **[JavaScript Fundamentals](Web_LWC/JavaScript.md):** ES6+ features, DOM manipulation, and asynchronous programming.
*   **[Lightning Web Components (LWC) Basics](Web_LWC/LWC_Basics.md):** Introduction to the LWC component bundle and local development setup.
*   **[LWC Advanced - Day 2](Web_LWC/LWC_Day2.md):** Integrating Apex with LWC via the `@wire` service and imperative calls.
*   **[LWC Communication - Day 3](Web_LWC/LWC_Day3.md):** Parent-Child communication, Custom Events, and Lightning Message Service (LMS).
*   **[LWC Specialized Features - Day 4](Web_LWC/LWC_Day4.md):** Advanced LDS (Lightning Data Service), NavigationMixin, and reusable Multi-component Case Studies.


---

## 🚀 How to Use This Documentation
Each file is organized into logical sections with clear explanations and code snippets. Whether you are an Admin looking to master security or a Developer diving into LWC, these notes serve as a centralized knowledge base.

*   **For Admins:** Start with [SFDC Introduction](Admin/SFDC_Intro.md) and [Security](Admin/Security.md).
*   **For Developers:** Dive into [Apex Basics](Development/Apex_Basics.md) and the [LWC Series](Web_LWC/LWC_Basics.md).


---

*Documentation maintained for professional Salesforce learning and reference.*
