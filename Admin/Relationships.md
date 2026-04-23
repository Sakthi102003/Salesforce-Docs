# Salesforce Relationships and Data Modeling

## Object Relationships
Relationships in Salesforce define how records from different objects are linked together.

### 1. Lookup Relationships
Provides a loose link between two objects.
- **Position & Job Application:** Position (Parent) $\to$ Job Application (Child).
- **Position & User:** User (Parent/Hiring Manager) $\to$ Position (Child).

### 2. Master-Detail Relationships
Provides a tight link between two objects where the child's (detail) existence depends on the parent (master).
- **Position & Interviewer:** Position (Master) $\to$ Interviewer (Detail).
- **Job Application & Review:** Job Application (Master) $\to$ Review (Detail).

### 3. Many-to-Many Relationships (Junction Objects)
Used when a record in one object can be related to many records in another, and vice versa.
- **Scenario:** A **Position** can be posted on multiple **Job Posting Sites**, and a site can host multiple positions.
- **Implementation:** Create a **Junction Object** (e.g., `Job Posting`) with two Master-Detail relationships:
  - One to the **Position** object.
  - One to the **Job Posting Site** object.

---

## Data Modeling Tools

### Lookup Filters
Used to restrict the parent records available for selection in a lookup or master-detail field.
- **Benefit:** Improves data quality and system efficiency by only showing relevant records to the user.
- **Scenario:** Filtering out inactive recruiters or only showing positions that match a candidate's skill set.

### Schema Builder
A graphical tool used to:
1. **Visualize:** View the data model and relationships of an application.
2. **Create:** Rapidly add new objects and fields to the schema.

---

## User Interface and Security

### Page Layouts
Page layouts control the organization and visibility of fields, buttons, and related lists for a record.
- **Customization Options:**
  - Marking fields as Required or Read-Only.
  - Hiding sensitive fields or irrelevant related lists.
  - Adding custom buttons, links, and quick actions.
- **Scenario:** Creating different layouts for **Recruiters** (hidden salary details) and **Recruiting Managers** (full visibility).

---

## Formula Fields
Calculated fields that automatically update based on other fields.

### Logic Scenarios:
1. **Days Open:** Calculate the number of days a position has remained open.
2. **Demand Level:** Display "High" for salaries $\ge \$120k$, "Low" for $\$40k-\$60k$, and "Medium" otherwise.
3. **Cross-Object Formulae:** Referencing fields from a related object (e.g., displaying the Hiring Manager's email on a Job Application record).
   - *Requirement:* Objects must be linked via a Lookup or Master-Detail relationship.