# Apex Triggers

## Overview
An **Apex Trigger** is a piece of code that executes automatically before or after a Data Manipulation Language (DML) event occurs, such as an insert, update, delete, or undelete.

### Trigger vs. Flow
- **Record-Triggered Flow:** Always prioritized for standard automation. It offers two main types:
  - **Before Save (Fast Field Updates):** Used for updating fields on the same record that triggered the flow.
  - **After Save (Actions and Related Records):** Used for creating or updating related records and performing actions like sending emails.
- **Apex Triggers:** Used when the business logic is too complex to be handled by declarative tools like Flows.

---

## Trigger Events
Apex triggers can respond to seven distinct events:
1. `before insert`
2. `after insert`
3. `before update`
4. `after update`
5. `before delete`
6. `after delete`
7. `after undelete`

### Syntax
```apex
trigger TriggerName on ObjectName (event1, event2) {
    // Logic here or call to a handler class
}
```

---

## Context Variables
Context variables provide information about the runtime state of the trigger:
- **`Trigger.new`:** A list of the new versions of the records being processed.
- **`Trigger.old`:** A list of the old versions of the records (available in update and delete events).
- **`Trigger.newMap`:** A map of IDs to the new versions of the records.
- **`Trigger.oldMap`:** A map of IDs to the old versions of the records.

---

## Trigger Types and Best Practices

### Before Triggers
Used to validate data or update fields on the record before it is saved to the database. These are more efficient for same-record updates as they avoid an additional DML call.

### After Triggers
Used to perform actions on related records or external systems after the record is saved. This context is required when you need the record's ID (which is generated upon saving).

---

## Real-World Scenarios

### Scenario 1: Field Update (Before Insert)
**Goal:** Automatically set the status of a new Position record to "New" before it is saved.

```apex
// Best Practice: Use a Handler Class
trigger PositionTrigger on Position__c (before insert) {
    PositionHandler.updateStatus(Trigger.new);
}

public class PositionHandler {
    public static void updateStatus(List<Position__c> posList) {
        for(Position__c pos : posList) {
            pos.Status__c = 'New';
        }
    }
}
```

### Scenario 2: Validation (Before Delete)
**Goal:** Prevent the deletion of Position records that are currently "Open."

```apex
trigger PositionTrigger on Position__c (before delete) {
    PositionHandler.avoidDeletingOpenPositions(Trigger.old);
}

public class PositionHandler {
    public static void avoidDeletingOpenPositions(List<Position__c> oldPosList) {
        for(Position__c pos : oldPosList) {
            if(pos.Status__c == 'Open') {
                pos.addError('Open positions cannot be deleted.');
            }
        }
    }
}
```

### Scenario 3: Validation (Before Insert/Update with External Data)
**Goal:** Prevent setting a Position's start date on a company holiday.

```apex
trigger HolidayTrigger on Position__c (before insert, before update) {
    PositionHolidayHandler.validateStartDate(Trigger.new, Trigger.oldMap);
}

public class PositionHolidayHandler {
    public static void validateStartDate(List<Position__c> newPosList, Map<Id, Position__c> oldPosMap) {
        Set<Date> allHolidays = new Set<Date>();
        for(Holiday h : [SELECT ActivityDate FROM Holiday]) {
            allHolidays.add(h.ActivityDate);
        }

        for(Position__c pos : newPosList) {
            // Only validate if the start date has changed or is new
            if(oldPosMap == null || oldPosMap.get(pos.Id).Start_Date__c != pos.Start_Date__c) {
                if(allHolidays.contains(pos.Start_Date__c)) {
                    pos.Start_Date__c.addError('Position start date cannot be a holiday.');
                }
            }
        }
    }
}
```

---

## Complex Concepts

### After Trigger Actions (Sharing)
**Scenario:** Grant edit access to the Hiring Manager once a Position status becomes "Open."
To achieve this, use the Share object (e.g., `Position__share`). This requires the Position OWD to be set to **Private**.

### Bulkification
Always design triggers to handle multiple records at once. Avoid putting SOQL queries or DML statements inside loops to prevent hitting governor limits.

---

## Quick Reference: Variable Availability
| Event | `Trigger.new` | `Trigger.old` | `Trigger.newMap` | `Trigger.oldMap` |
|---|:---:|:---:|:---:|:---:|
| **Before Insert** | Yes | No | No | No |
| **After Insert** | Yes | No | Yes | No |
| **Before Update** | Yes | Yes | Yes | Yes |
| **After Update** | Yes | Yes | Yes | Yes |
| **Before Delete** | No | Yes | No | Yes |
| **After Delete** | No | Yes | No | Yes |
| **After Undelete** | Yes | No | Yes | No |