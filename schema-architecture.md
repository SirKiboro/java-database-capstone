# Smart Clinic Management System: Architecture Design

## 1. Architecture Summary

The Smart Clinic Management System follows a three-tier architecture consisting of the Presentation Layer, Application Layer, and Data Layer. The Presentation Layer uses Thymeleaf templates to render HTML dashboards and forms, while REST APIs provide JSON-based communication for external clients. The Application Layer uses Spring Boot and follows the Model-View-Controller (MVC) pattern, with MVC controllers handling browser requests and REST controllers exposing API endpoints. The business logic is managed by service classes, which communicate with the Data Layer through repositories. MySQL stores structured clinic information using Spring Data JPA and Hibernate, while MongoDB stores document-oriented data using Spring Data MongoDB. This separation improves maintainability, supports multiple client interfaces, and allows each database to handle the data it is best suited for.

## 2. Numbered Flow

1. **User initiates a request:** A user interacts with the clinic's HTML dashboard, submits a form, or sends a request to a REST API endpoint.

2. **Request reaches the controller:** Spring Boot receives the HTTP request and routes it to the appropriate MVC controller or REST controller based on the URL and HTTP method.

3. **Controller processes the request:** The controller extracts request parameters, form data, or JSON payloads and performs any required initial validation.

4. **Business logic executes:** The controller delegates the operation to the appropriate service class, where business rules and application logic are applied.

5. **Service accesses the data layer:** The service calls the appropriate repository to retrieve, create, update, or delete information.

6. **Database operation is performed:** For structured relational data, Spring Data JPA and Hibernate interact with MySQL. For document-oriented data, Spring Data MongoDB communicates with MongoDB.

7. **Database returns the result:** The selected database executes the operation and returns the retrieved records, the updated entity, or the operation result through its repository.

8. **Service returns the result:** The service processes the repository response and returns the required data or outcome to the controller.

9. **Controller prepares the response:** An MVC controller adds the required data to the model and returns a Thymeleaf view name for HTML rendering. A REST controller serializes the response as JSON and returns the appropriate HTTP status code.

10. **Response reaches the client:** Spring Boot sends the rendered HTML page or JSON response to the browser or API client, where the result is displayed or consumed.
