# Salesforce Flows and Approval Processes

## Approval Processes
An **Approval Process** is an automated process your organization uses to approve records in Salesforce.

### Scenarios:
1. **Simple Approval:** New Position records are routed to 'Mario Ruiz' for approval.
2. **Multi-Step Approval:**
   - **Step 1:** If a Position is "New," it is routed to 'Mario Ruiz'.
   - **Step 2:** If the Position's Pay Grade is $\ge 300$, it is also routed to the VP of Human Resources.
3. **Skipping Steps:** Logic configured to bypass certain approval steps based on specific criteria.

### Supporting Structures:
- **Queues:** A collection of records that do not have an individual owner. Users who are members of the queue can "pick up" these tasks.
  - *Example Queues:* Director Queue, Hiring Manager Queue, Recruiter Queue.
- **Public Groups:** A set of users used to simplify the sharing of records, folders, and other content.

---

## Salesforce Flows
Flows are powerful automation tools used to collect data and perform actions in Salesforce.

### 1. Screen Flows
These flows provide a user interface (screens) to collect information from users.
- **Scenario:** A screen flow where users enter Candidate details (Name, Phone, Email, Current Employer) which are then saved as a new record.
- **Deployment ("Surfacing"):**
  - As a **Quick Action** on a related record (e.g., Job Application).
  - Directly on a **Home Page**, **Record Page**, or **App Page**.

### 2. Record-Triggered Flows
These flows run automatically in the background when a record is created, updated, or deleted.

#### Core Configuration:
- **Object:** The specific Salesforce object that triggers the flow.
- **Trigger Event:** 
  - Created (Insert)
  - Updated (Update)
  - Created or Updated (Upsert)
  - Deleted (Delete)
- **Entry Conditions:** Criteria that must be met for the flow to execute.

#### Types of Record-Triggered Flows:
1. **Before-Save (Fast Field Updates):**
   - Executes *before* the record is committed to the database.
   - Ideal for updating fields on the same record that triggered the flow.
   - *Note:* In an "Insert" event, the record ID is not yet available.
2. **After-Save (Actions and Related Records):**
   - Executes *after* the record is committed.
   - Used for performing actions (e.g., sending emails) or updating related records.
   - *Note:* The record ID is available here.

#### Common Actions:
- Sending Emails
- Updating related fields
- Automatically submitting records for approval
- Calling other Flows or Apex classes
- Posting to Chatter

---

## UI Design in Salesforce
- **Salesforce Classic:** A traditional, page-based layout similar to basic HTML.
- **Salesforce Lightning:** A modern, component-based framework.
  - **Home Page:** The landing page for users.
  - **Record Page:** The layout used when viewing a specific record (e.g., a specific "Position").
  - **App Page:** A custom page built for a specific application.