# Salesforce Integration and SDLC

## Integration
**Integration** is the process of connecting a Salesforce organization with another Salesforce organization or an external application to exchange data and functionality.

### Core Integration Methods:
1. **Salesforce Connect:** A declarative tool used to connect two Salesforce organizations, allowing users to view and search external data via external objects and lookups.
2. **APIs (Application Programming Interfaces):**
   - **SOAP API (Simple Object Access Protocol):** Uses XML for data exchange. It is highly structured and supports formal contracts (WSDL).
   - **REST API (Representational State Transfer):** Built on the HTTP protocol (Client-Server architecture). It supports both JSON and XML and is known for being lightweight and flexible.

### Web Services in Apex
- **Exposing a Web Service:** Making an Apex class accessible to external systems. This is done by marking the class as `global` and using the `@RestResource` or `webservice` keywords.
- **Consuming a Web Service (HTTP Callout):** Making a request from Salesforce to an external API (e.g., fetching weather data or currency rates).

---

## Software Development Life Cycle (SDLC)
The SDLC represents the stages involved in software creation:
1. **Requirements Gathering:** Understanding what the business needs.
2. **Analysis:** Determining the technical feasibility.
3. **Design:** Planning the architecture and UI.
4. **Development:** Writing the code (Apex, LWC, etc.).
5. **Testing:** Verifying the functionality.
6. **Deployment:** Moving code to the Production environment.
7. **Maintenance:** Providing ongoing support and updates.

---

## Testing and Deployment

### Environments
- **Sandbox:** A copy of the Production environment used for development and testing. New code is always built here first.
- **Production:** The live environment where end-users interact with the application.

### Why Testing is Critical:
- **Code Quality:** Ensures the code handles various user inputs correctly.
- **Deployment Requirement:** Salesforce requires a minimum of **75% code coverage** for all Apex classes and triggers before they can be deployed to Production.

### Test Essentials:
- **`@isTest` Annotation:** Identifies a class or method as a test.
- **`System.assertEquals(expected, actual)`:** A standard method used to compare the expected outcome with the actual result. If they match, the test passes.
- **Unit Testing:** Testing small, individual pieces of code in isolation.