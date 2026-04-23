# Apex Basics

## Module 10: Sandbox
A **Sandbox** is a copy of the Production environment used for testing, development, and customization before deployment.

### Key Characteristics:
- It is a copy of the Production environment.
- Salesforce provides two primary types of environments:
  - **Production Environment:** Used by end-users for live operations.
  - **Sandbox Environment:** Used for development and testing purposes (e.g., creating objects, fields, flows, validations, Apex classes, and Apex triggers).

### Accessing the Sandbox:
- **Login URL:** [https://test.salesforce.com/](https://test.salesforce.com/)
- Use dedicated Sandbox credentials to log in.

---

## Module Overview
- **Module 11:** Apex Classes
- **Modules 12 & 13:** Setting up Visual Studio Code
- **Module 14:** SOQL and SOSL
- **Module 15:** Apex Triggers
- **Basics:** HTML, CSS, and JavaScript
- **LWC:** Lightning Web Components (5-day deep dive)
- **Advanced Topics:** Apex Testing, Integration, and Asynchronous Apex
- **Capstone:** Final Case Study (3 days)

---

## Apex Programming Language
Apex is a strongly-typed, object-oriented programming language designed for the Salesforce platform.

### Core Features:
1. **Object-Oriented:** Supports classes, interfaces, and inheritance.
2. **Strongly-Typed:** Data types (e.g., Integer, String, Double) are defined and checked at compile time.
   - *Note:* Languages like Python and JavaScript are dynamically typed, where types are determined at runtime.

### Access Specifiers:
1. **Public:** Accessible throughout the organization.
2. **Private:** Accessible only within the class where they are defined. Methods and variables can be private, but top-level classes cannot.
3. **Protected:** Accessible to the defining class and any subclasses (used in inheritance).
4. **Global:** Accessible outside the organization. This is primarily used for integration purposes.

---

## Collections in Apex
While **Arrays** have a fixed size (e.g., `Integer[] arr = new Integer[20];`), **Collections** are dynamic in size.

### Types of Collections:
1. **List:** An ordered collection that allows duplicate elements.
   - `add(element)`: Adds an element to the end of the list.
   - `add(index, element)`: Inserts an element at a specific index (starting from 0).
   - `set(index, element)`: Replaces the element at a specific index.

2. **Set:** An unordered collection that does not allow duplicate elements. Elements are stored in their natural sort order.

3. **Map:** Stores data in unique Key-Value pairs. Keys must be unique, but values can be duplicated.
   - `put(key, value)`: Adds an entry to the map.
   - `keySet()`: Returns a set of all keys in the map.
   - `values()`: Returns a list of all values in the map.

---

## sObjects (Salesforce Objects)
An `sObject` is a generic data type used to store Salesforce records.

### Categories:
1. **Specific sObject:** Stores a record for a specific object.
   - Example: `Account a;`, `Contact con;`, `Position__c pos;`
2. **Generic sObject:** Can store a record from any Salesforce object.
   - Example: `sObject s;`

---

## Object-Oriented Principles in Apex

### Encapsulation
Uses properties with `get` and `set` accessors to control data visibility and modification.

### Inheritance
Allows a class to access methods and variables from another class using the `extends` keyword.

```apex
class A {
    Integer num;
    public void ABC() {
        // Method implementation
    }
}

class B extends A {
    Integer num1;
    public void DEF() {
        // Method implementation
    }
}
```