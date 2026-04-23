# Salesforce Object Query Language (SOQL)

## Introduction to SOQL
SOQL is used to search your organization's Salesforce data for specific information. It is similar to standard SQL but optimized for the Salesforce multi-tenant environment.

### Key Differences from SQL:
- **No `SELECT *`:** You must explicitly specify the fields you want to retrieve. Alternatively, in newer API versions, you can use `FIELDS(ALL)`, `FIELDS(STANDARD)`, or `FIELDS(CUSTOM)`.
- **Relationship Queries:** SOQL does not support traditional `JOIN` statements. Instead, it uses relationship traverse notation (e.g., `Account.Name`) or nested subqueries.
- **Return Types:** Queries can return a single `sObject`, a `List<sObject>`, an `Integer` (for count queries), or an `AggregateResult` (for grouped data).

---

## Basic Query Syntax and Examples

### 1. Simple Selection
```sql
SELECT Name, Industry, AnnualRevenue FROM Account WHERE Name = 'Edge Communications'
```

### 2. Filtering and Comparison
- **Logical Operators:** `AND`, `OR`, `NOT`, `IN`, `LIKE`.
- **Null Handling:** `NULLS FIRST`, `NULLS LAST`.
```sql
-- Fetch candidates with 5 to 10 years of experience
SELECT First_Name__c, Last_Name__c FROM Candidate__c WHERE Years_of_Experience__c > 5 AND Years_of_Experience__c < 10

-- Use 'IN' for multiple values
SELECT Name, Status__c FROM Job_Application__c WHERE Status__c IN ('Open', 'Hold')
```

### 3. Ordering and Limits
```sql
-- Top 5 opportunities by amount
SELECT Name, Amount FROM Opportunity ORDER BY Amount DESC LIMIT 5
```

---

## Relationship Queries
Relationship queries allow you to retrieve data from related objects in a single call.

### 1. Child-to-Parent Queries
Used to fetch data from the child object and include fields from its parent.
- **Standard Objects:** Use dot notation (`Account.Name`).
- **Custom Objects:** Use `__r` suffix on the relationship field (`Position__r.Name`).
```sql
-- Standard objects: Contact to Account
SELECT FirstName, LastName, Account.Name FROM Contact

-- Custom objects: Job Application to Position
SELECT Name, Status__c, Select_Position__r.Name FROM Job_Application__c
```

### 2. Parent-to-Child Queries
Used to fetch a parent record and all its related child records in a nested subquery.
- **Standard Objects:** Use the plural relationship name (e.g., `Contacts`).
- **Custom Objects:** Use the relationship name followed by `__r` (e.g., `Job_Applications__r`).
```sql
-- Account and its related Contacts
SELECT Name, (SELECT FirstName, LastName FROM Contacts) FROM Account

-- Position and its related Job Applications
SELECT Name, (SELECT Name, Status__c FROM Job_Applications__r) FROM Position__c
```

---

## SOQL in Apex

### Using Variables in Queries (Binding)
Use the colon (`:`) prefix to reference Apex variables within a SOQL string.
```apex
public class PositionService {
    public static void getPositionsByPriority(String status) {
        List<Position__c> posList = [SELECT Name FROM Position__c WHERE Priority__c = :status];
        System.debug(posList);
    }
}
```

### Handling Aggregate Results
When using `GROUP BY` or aggregate functions, the query returns an `AggregateResult` object.
```apex
List<AggregateResult> results = [SELECT Industry, SUM(AnnualRevenue) totalRev FROM Account GROUP BY Industry];
for (AggregateResult ar : results) {
    System.debug('Industry: ' + ar.get('Industry') + ' Total: ' + ar.get('totalRev'));
}
```

### sObject Data Types
- **Specific sObject:** `Position__c pos;` (Can only hold Position records).
- **Generic sObject:** `sObject obj;` (Can hold a record of any type).
```apex
sObject genericObj;
genericObj = [SELECT Name FROM Account LIMIT 1]; // Valid
genericObj = [SELECT Name FROM Position__c LIMIT 1]; // Also valid
```