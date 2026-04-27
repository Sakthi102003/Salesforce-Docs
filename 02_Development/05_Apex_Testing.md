# Apex Testing

In Salesforce, unit tests are essential to ensure the reliability and quality of your code.

## Core Concepts
- **`@isTest` Annotation:** Used to define classes or methods that contain test code.
- **Code Coverage:** To deploy Apex code to a Production environment, at least **75%** of the code must be covered by unit tests.

---

## Test Data Management
Test data consists of Salesforce records used to verify functionality. There are three primary ways to manage test data:

1. **Inline Creation:** Create test records directly within the individual test method.
2. **`@testSetup` Method:** Create common test data once in a dedicated method. This data is then available to all test methods in the class, improving performance and maintainability.
3. **`seeAllData=true`:** Allows test methods to access the actual data within the organization.
   - **Important:** Using `seeAllData=true` is generally **not a best practice**. It can lead to inconsistent results and dependency on environment state. It should only be used in exceptional cases where accessing live data is unavoidable.

*Note:* Data created during test execution is **never committed** to the database; it is automatically rolled back once the test finishes.

---

## Execution Contexts

### System Context
By default, Apex tests run in the **System Context**, meaning they ignore user-level permissions, field-level security, and Organization-Wide Defaults (OWD).

### User Context (`System.runAs`)
The `System.runAs` method allows you to execute code blocks as a specific user. This is crucial for verifying that your code respects the profiles, permissions, and sharing settings of different users.

---

## Governor Limits in Testing
Salesforce enforces strict governor limits on resource usage (e.g., SOQL queries and DML operations).

- **SOQL Limit:** 100 queries per transaction.
- **DML Limit:** 150 operations per transaction.

### `Test.startTest()` and `Test.stopTest()`
These methods provide a fresh set of governor limits for the code executed between them. This helps ensure that the setup logic doesn't count against the limits of the functionality being specifically tested.
- `Test.stopTest()` also ensures that any asynchronous calls (like `@future` methods) are completed before the test continues.