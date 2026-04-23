# Salesforce (SFDC) Introduction

## Course Roadmap
- **Days 1–7:** Declarative Development (Configuring the platform using built-in tools; no coding required).
- **Days 8–9:** Agile Methodology and Git Version Control.
- **Day 10–Finish:** Programmatic Development (Apex, SOQL, SOSL, DML, and LWC).

---

## Cloud Computing Basics
**Cloud Computing** is the delivery of computing services—including servers, storage, databases, networking, software, and analytics—over the internet ("the cloud").

### Cloud Service Models:
1. **SaaS (Software as a Service):** Applications delivered over the web (e.g., Google Docs, Salesforce.com).
2. **PaaS (Platform as a Service):** A platform for developers to build, test, and deploy applications (e.g., Force.com, Heroku).
3. **IaaS (Infrastructure as a Service):** Fundamental computing resources like virtual machines and storage (e.g., AWS, Azure).

---

## What is CRM?
**Customer Relationship Management (CRM)** is a technology for managing all your company's relationships and interactions with customers and potential customers. Organziations use CRM to stay connected to customers, streamline processes, and improve profitability.

### Salesforce as a CRM:
Salesforce provides specialized "Clouds" for different business functions:
- **Sales Cloud:** Helps sales teams close deals faster.
- **Service Cloud:** Supports customer service agents in resolving cases.
- **Marketing Cloud:** Allows marketers to create personalized customer journeys.

---

## Salesforce Core Concepts

### 1. The Salesforce Org
An "Org" (Organization) is a specific instance of Salesforce used by a company for its daily business.

### 2. Apps, Objects, and Fields
- **App:** A collection of tabs and functionality designed for a specific business process (e.g., a "Recruiting App").
- **Object:** A database table. Objects can be **Standard** (provided by Salesforce like Account or Contact) or **Custom** (created by developers like Position__c).
- **Field:** A column in the database table.
- **Record:** A single row in the database table (an individual piece of data).

### 3. MVC Architecture
Salesforce follows the **Model-View-Controller** pattern:
- **Model:** The data and database schema (Objects and Fields).
- **View:** The user interface (Page Layouts, Lightning Components).
- **Controller:** The logic that connects the view and the model (Apex code, Flows).

---

## Salesforce Architecture

### Multi-Tenancy
Salesforce is a multi-tenant platform, meaning many different companies (tenants) share the same underlying infrastructure.
- **Governor Limits:** To ensure that one company's code doesn't monopolize shared resources (like CPU or memory), Salesforce enforces strict execution limits.

### Record Identifiers
Every record in Salesforce has a unique **Record ID** (Primary Key). These IDs are either 15 characters (case-sensitive) or 18 characters (case-insensitive).

---

## Object Relationships
Relationships associate one object with another to create a comprehensive data model.

### 1. One-to-Many Relationships
- **Lookup Relationship:** A loose link. The child record remains if the parent is deleted. Not mandatory.
- **Master-Detail Relationship:** A tight link. The child depends entirely on the parent. If the parent is deleted, the child is also deleted.

| Feature | Lookup | Master-Detail |
|---|---|---|
| **Dependency** | Loosely Coupled | Tightly Coupled |
| **Mandatory** | No | Yes |
| **Deletion** | Parent deletion keeps child | Parent deletion deletes child |
| **Roll-up Summary** | Not supported | Supported |
| **Ownership** | Can have different owners | Child inherits parent's owner |

### 2. Many-to-Many Relationships
Implemented using a **Junction Object**. A junction object is a custom object with two master-detail relationships.
- **Scenario:** A Position can be posted on multiple Job Posting Sites; a Site can host many Positions.
- **Junction Object:** `Job_Posting__c` connects `Position__c` and `Site__c`.

---

## Data Tools and UI
- **Picklist:** A dropdown field.
- **Global Value Set:** A reusable set of values that can be shared across multiple picklists in several objects (e.g., "Priority Levels: High, Medium, Low").
- **Field Dependency:** A filter that changes the values in one picklist (dependent) based on the selection in another (controlling).