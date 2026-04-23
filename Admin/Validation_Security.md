# Validation and Security

## Module 3: Fields and Validation
**Day 4 Overview:**
- Formula Fields (Simple, Advanced, and Cross-Object)
- Roll-up Summary Fields
- Validation Rules
- Debug Logs

### Cross-Object Formula Fields
**Scenario:** Create a formula field on the **Candidate** object named `Eligible for Hiring` that returns "Yes" or "No" based on criteria from related objects.
- **Position Object:** Contains a checkbox field `Immediate Required`.
- **Candidate Object:** Contains a field `Notice Period` with values like 10, 15, or 30 days.

### Roll-up Summary Fields
- **Read-Only:** These fields are automatically calculated and cannot be edited manually.
- **Master-Detail Relationship:** Can only be created on the **Master (Parent)** object to summarize data from **Detail (Child)** records.
- **Aggregate Functions:**
  - `Sum()`
  - `Count()`
  - `Min()`
  - `Max()`

**Example:**
Create a Roll-up Summary field on the **Job Application** object to count the number of **Reviews** where the candidate's experience is greater than 3 years.
- **Master:** Job Application
- **Detail:** Review

---

## Validation Rules
Validation rules verify that the data a user enters into a record meets the standards you specify before the user can save the record.

### Regular Expressions (REGEX)
Used to create patterns for data validation (e.g., phone numbers or IDs).
- `[]`: Defines allowed characters (e.g., `[0-9]` allows any digit).
- `+`: Matches one or more occurrences (e.g., `[0-9]+`).
- `*`: Matches zero or more occurrences.
- `?`: Matches zero or one occurrence.
- `{}`: Matches a fixed number of characters (e.g., `[0-9]{4}`).

**Examples:**
- **Names:** `[a-zA-Z]+`
- **ID Pattern:** `[0-9]{4}-[0-9]{4}-[0-9]{4}` (e.g., 6576-5764-5376)

**Scenario:**
Ensure the `State/Province` field contains exactly 2 characters.
- **Formula:** `NOT(REGEX(State_Province__c, "[A-Za-z]{2}"))`
- *Note:* `REGEX()` function is only compatible with Text fields.

**Scenario:**
Restrict users from changing the `Status` of a Position incorrectly:
- Prevent moving from `Open` back to `New`.
- Prevent moving from `Closed` back to `New` or `Open`.

---

## Module 4: Data Security
Salesforce security is layered, controlling access to Apps, Tabs, Objects, Fields, and individual Records.

### Security Levels:
1. **Organization-Level Security:** Controls when and from where users can log in.
2. **Object-Level Security:** Controls whether a user can see, create, edit, or delete records of a specific object.
3. **Field-Level Security:** Controls whether a user can see or edit a specific field on an object.
4. **Record-Level Security:** Controls which individual records a user can access.

### User Management
- **User License:** Determines which features the user can access. Each user must have exactly one license.
- **Profile:** Assigned to a user based on their license. It defines their base permissions and access levels.
- **Freezing vs. Deactivating a User:**
  - **Freezing:** Prevents the user from logging in, but their license remains occupied. Used when deactivating isn't immediately possible (e.g., if the user is part of a hierarchy).
  - **Deactivating:** Prevents login AND releases the license so it can be assigned to someone else.

### 1. Organization-Level Security
- **Password Policies:** Set requirements for password complexity and expiration.
- **Login IP Ranges:** Restrict login access to specific network addresses.
- **Login Hours:** Restrict login access to specific times of the day.

### 2. Object-Level Security
Managed via **Profiles** and **Permission Sets**.

**Profiles:**
- **Standard Profiles:** Predefined by Salesforce; object permissions cannot be modified.
- **Custom Profiles:** Created by cloning a standard profile; permissions can be fully customized.
- *Best Practice:* Never create a profile from scratch; always clone an existing one.

**Common Permissions:**
- Read
- Create
- Edit
- Delete
- View All (Override sharing)
- Modify All (Override sharing)