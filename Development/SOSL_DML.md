# Salesforce Search (SOSL) and Data Manipulation (DML)

## Salesforce Object Search Language (SOSL)
SOSL is used to perform text-based searches across multiple objects simultaneously. It is the engine behind the Global Search bar in the Salesforce UI.

### Syntax and Keywords:
- **`FIND`:** The primary keyword followed by the search term.
  - In Apex: `FIND 'Edge'`
  - In Query Editor: `FIND {Edge}`
- **`IN` (Search-Group):** Restricts the search to specific field types.
  - `ALL FIELDS` (Default)
  - `NAME FIELDS`
  - `EMAIL FIELDS`
  - `PHONE FIELDS`
- **`RETURNING`:** Specifies which objects and fields to return in the results.

### Example (Query Editor):
```sql
FIND {Edge} IN ALL FIELDS RETURNING Account(Name), Contact(FirstName, LastName), Opportunity(Name, StageName)
```

### SOSL in Apex:
SOSL returns a "List of Lists" (`List<List<sObject>>`), where each inner list contains results for a specific object.
```apex
List<List<sObject>> searchList = [FIND 'Edge' IN ALL FIELDS RETURNING Account(Name), Contact(FirstName, LastName)];
List<Account> accounts = (List<Account>)searchList[0];
List<Contact> contacts = (List<Contact>)searchList[1];
```

---

## Data Manipulation Language (DML)
DML statements allow you to manage records in the database.

### Core Operations:
- **`insert`:** Creates new records.
- **`update`:** Modifies existing records.
- **`upsert`:** Creates new records or updates existing ones based on a unique identifier.
- **`delete`:** Moves records to the Recycle Bin.
- **`undelete`:** Restores records from the Recycle Bin.
  - *Tip:* Use the `ALL ROWS` keyword in SOQL to query records including those in the Recycle Bin.
- **`merge`:** Combines up to three duplicate records into one.

### Transaction Modes:
1. **Simple DML:** Operates on a single record.
2. **Bulk DML (All-or-None):** Uses a list of records. If a single record fails, the entire transaction is rolled back (no records are saved).
3. **Database Methods (Partial Success):** Allows successful records to be saved even if others in the list fail.
   - `Database.insert(recordList, false)`: The second parameter (`allOrNone`) set to `false` enables partial success.

---

## Multi-Tenancy and Governor Limits
Salesforce uses a **Multi-Tenant Architecture**, where multiple customers share the same physical resources.
- **Governor Limits:** To ensure fair resource allocation, Salesforce imposes strict limits on the number of SOQL queries (100 per transaction) and DML statements (150 per transaction) that can be executed in a single execution context.