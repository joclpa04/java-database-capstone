Section 1: Architecture summary
This Spring Boot application uses both MVC and REST controllers. 
Thymeleaf templates are used for the Admin and Doctor dashboards, while REST APIs serve all other modules. 
The application interacts with two databases—MySQL (for patient, doctor, appointment, and admin data) and MongoDB (for prescriptions). 
All controllers route requests through a common service layer, which in turn delegates to the appropriate repositories. 
MySQL uses JPA entities while MongoDB uses document models.

Section 2: Numbered flow of data and control
User accesses the system through web dashboards (AdminDashboard, DoctorDashboard) or API-based modules (Appointments, PatientDashboard, PatientRecord).
The request is routed to the appropriate controller depending on the URL and HTTP method, reaching either a Thymeleaf Controller (for HTML views) or a REST Controller (for JSON responses).
The controller processes the request and calls the Service Layer, which contains the core business logic and validation rules.
The Service Layer executes application workflows and coordinates operations such as verifying doctor availability or validating appointment data.
The Service Layer interacts with the Repository Layer to perform data access operations.
Repositories communicate with the databases, using MySQL (via Spring Data JPA) for structured entities like patients, doctors, and appointments, and MongoDB (via Spring Data MongoDB) for flexible documents such as prescriptions.
Retrieved data is mapped to application models and returned to the client, where Thymeleaf controllers render dynamic HTML pages for browsers and REST controllers return JSON responses for API consumers.
