# Salesforce Data Security and Automation

## Data Security Model
Salesforce provides a robust, multi-layered security model to control access to data at the organization, object, field, and record levels.

---

## 1. Object-Level and Field-Level Security
These controls determine which objects and individual fields a user can access and whether they can create, edit, or delete them.

### Profiles and Permission Sets
- **Profiles:** Define the **minimum level of access** for a specific job function (e.g., "Recruiter"). Every user must have exactly one profile.
- **Permission Sets:** Used to grant **additional access** beyond the base profile. This allows for flexible security without creating dozens of unique profiles.
- **Permission Set Groups:** Clustered collections of permission sets that can be assigned to users as a single unit. Use **Muting Permission Sets** within a group to exclude specific permissions for certain users.

---

## 2. Record-Level Security
Once object and field access are granted, record-level security determines exactly which individual records a user can see and edit.

### Implementation Methods (The "Security Waterfall"):
1. **Organization-Wide Defaults (OWD):** The baseline level of access.
   - **Private:** Only the record owner (and those above them in the hierarchy) can see the record.
   - **Public Read Only:** Everyone can see all records, but only the owner can edit.
   - **Public Read Write:** Everyone can see and edit all records.
2. **Role Hierarchy:** Automatically grants record access to users positioned above the record owner in the management hierarchy.
3. **Sharing Rules:** Exceptions to OWD that allow for automatic sharing based on specific criteria (e.g., "Share all 'High Priority' positions with the Global Recruitment Team").
4. **Manual Sharing:** Allows users to share a single record with another user or group using the "Sharing" button on the record page.

---

## 3. Automation Tools

### Approval Processes
An automated sequence used to secure approval for records from designated managers or stakeholders.
- **Initial Submission Actions:** Actions performed immediately when a user submits a record (e.g., locking the record, sending an email alert, or updating a 'Status' field).
- **Approval Steps:** Defines the chain of approvers. A process can have multiple steps, but at least one is required for activation.
- **Final Actions:** Actions taken once a record is fully approved or rejected.

### Salesforce Flows
The most powerful point-and-click automation tool in Salesforce.
- **Screen Flows:** Guides users through a business process with a custom UI.
- **Record-Triggered Flows:** Executes logic automatically when a record is created, updated, or deleted.

---

## 4. Auditing and Monitoring
- **Field History Tracking:** Tracks changes to specific fields on an object, capturing the previous value, new value, and the user who made the change.
- **Audit Trail:** Tracks recent setup changes made to the organization by administrators.
- **Transferring Records:** A tool for mass-changing the ownership of records from one user to another (e.g., when an employee leaves the company).