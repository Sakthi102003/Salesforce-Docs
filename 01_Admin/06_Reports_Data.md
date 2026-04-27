# Salesforce Reports, Dashboards, and Data Management

## Record-Triggered Flows
Record-triggered flows are used to automate processes when a record is created, updated, or deleted.

### 1. Before-Save Flows (Fast Field Updates)
- **Use Cases:**
  - **Validation:** Performing complex validations that exceed the capabilities of standard Validation Rules.
  - **Same-Record Updates:** Updating fields on the triggering record itself (e.g., if Pay Grade is 400, set Priority to "Critical").
- **Efficiency:** These are significantly faster than After-Save flows because they execute before the record is saved to the database, avoiding unnecessary DML operations.

### 2. After-Save Flows (Actions and Related Records)
- **Use Cases:**
  - **Related-Record Updates:** Updating fields on objects related to the triggering record (e.g., if a Position is filled, updating all related Job Applications to "Closed").
  - **Actions:** Performing complex tasks like sending emails, posting to Chatter, or submitting a record for approval.
- **Example Scenario:** Automatically submit a Position for approval when its status changes to "New."

---

## Data Management
Transferring data into and out of Salesforce is a core administrative task.

### Data Import and Export Tools:
1. **Data Import Wizard:** An internal Salesforce tool.
   - **Capacity:** Supports up to 50,000 records.
   - **Supported Actions:** Insert, Update, and Upsert.
   - **Requirement:** Files must be in `.csv` format.
2. **DataLoader.io:** A powerful external tool (powered by MuleSoft) for larger datasets and more complex mapping.

### Key Concepts:
- **Export vs. Export All:** 
  - **Export:** Retrieves only the active records currently in the object.
  - **Export All:** Retrieves active records plus items currently in the Recycle Bin (deleted records).
- **Common Import Errors:** Custom validation rule violations and field type mismatches.

---

## Reports and Dashboards

### Report Types
A **Report Type** defines the set of records and fields available to a report based on the relationships between a primary object and its related objects.
- **Standard Report Types:** Pre-built by Salesforce.
- **Custom Report Types:** Created by administrators to handle complex relationships (e.g., a report showing "Positions with Job Postings and Job Posting Sites").

### Report Formats:
1. **Tabular:** A simple list of records in rows and columns. (Note: Charts cannot be created from tabular reports).
2. **Summary:** Groups records by a specific field (e.g., by "Status"). Enables chart creation.
3. **Matrix:** Groups records by both rows and columns (e.g., by "Status" and "Department"). Excellent for comparing trends.
4. **Joined:** Combines multiple report types into a single view.

### Dashboards
A **Dashboard** is a visual representation of report data (using charts, gauges, etc.).
- **Folders:** Used to organize and secure access to reports and dashboards. 
- **Dynamic Dashboards:** Allows users to view the dashboard data as a specific user, ensuring they only see information relevant to their role and permissions.