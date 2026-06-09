# Cross-cutting Concepts

## 8.1 Authentication and Authorization

All access to the UMS is controlled through a unified authentication and authorization mechanism that applies to every module and every user group.

Authentication is handled via JSON Web Tokens (JWT). When a user logs in, the backend issues a signed JWT that the client includes in every subsequent request. The backend validates the token on each request without requiring server-side session storage, which supports stateless and scalable deployments.

Authorization is implemented using Role-Based Access Control (RBAC). Each user is assigned exactly one role at login. The available roles are:

| Role          | Description                                                                                           |
|---------------|-------------------------------------------------------------------------------------------------------|
| Student       | Can enroll in courses, view grades and attendance, access course materials, and manage personal data. |
| Lecturer      | Can record attendance, submit grades, upload course materials, and view their assigned courses.       |
| Administrator | Can manage users, courses, schedules, and generate reports.                                           |
| Finance Staff | Can manage billing, process payments, and access financial reports.                                   |

Every API endpoint in the Node.js backend declares the minimum required role. Requests from users with insufficient privileges are rejected with HTTP 403 before reaching the business logic.

The React frontend additionally hides UI elements that a user's role does not permit, reducing confusion and accidental navigation to restricted areas. This is a usability measure only — the backend authorization is always the authoritative enforcement point.

---

## 8.2 Input Validation and Error Handling

Input validation and consistent error handling are applied uniformly across all modules to ensure data integrity and provide predictable behavior for the frontend.

**Validation** is performed in two places:

- In the React frontend, forms validate user input before submission to give immediate feedback and reduce unnecessary network requests.
- In the Node.js backend, all incoming data is validated independently of the frontend. Frontend validation is never trusted as the sole check. Invalid requests return HTTP 400 with a structured error response.

**Error responses** follow a consistent structure across all API endpoints:

```json
{
  "status": 400,
  "error": "Validation failed",
  "details": ["Name must not be empty", "Student ID must be a positive integer"]
}
```

Unhandled exceptions are caught by a global exception handler in the Node.js middleware pipeline. This ensures that internal errors never expose stack traces or system details to the client. All unhandled exceptions are logged (see section 8.3) and return HTTP 500 with a generic error message.

---

## 8.3 Logging and Monitoring

Logging is applied consistently across all backend components. Every significant system event — incoming requests, authentication attempts, data modifications, integration calls to the FMS, and errors — is recorded in a structured log.

Log entries follow a consistent format including timestamp, log level, affected module, user identifier (where available), and a short description. Personally identifiable information such as names or contact details is not included in log output.

The application is deployed on AWS, which provides built-in monitoring and alerting capabilities. CloudWatch is used to collect logs, track availability, and alert the operations team when error rates or response times exceed defined thresholds.

Log levels used throughout the system:

| Level | Usage                                                                                         |
|-------|-----------------------------------------------------------------------------------------------|
| INFO  | Normal operations: logins, data reads, successful transactions                                |
| WARN  | Recoverable issues: failed login attempts, slow queries, FMS API retries                      |
| ERROR | Failures requiring attention: unhandled exceptions, FMS integration failures, database errors |

---

## 8.4 Data Persistence and Consistency

All persistent application data is stored in a centralized MongoDB database. The following principles apply across all modules:

**Collection ownership**: Each functional module manages its own MongoDB collections. Modules do not directly access collections owned by other modules. Instead, data is exchanged through the responsible service layer, preserving loose coupling between business domains.

**Data consistency**: Operations that affect multiple business entities, such as course enrollment together with billing creation, are executed as a single logical operation. If one single step fails, the entire operation is rolled back or compensated to avoid inconsistent application state.

**Data protection**: The MongoDB database is accessible only from the Node.js backend within the cloud infrastructure. It is not directly exposed to external users. Database credentials are managed through secure environment variables and are never stored in the application source code.

---

## 8.5 Scalability and Deployment

The UMS is deployed on AWS to meet the requirement of supporting high numbers of concurrent users, particularly during peak periods such as course enrollment phases and examination periods.

The deployment architecture supports horizontal scaling: multiple instances of the Node.js backend can run in parallel behind a load balancer. Because authentication is stateless (JWT, see section 8.1), no session synchronization between instances is required.

The React frontend is served as a static build from a CDN, reducing load on the application server for asset delivery.

The React frontend is delivered as static content, allowing efficient distribution and reducing the load on the application servers.

MongoDB can be deployed as a managed cloud database service, providing automated backups, replication, and high availability. The cloud infrastructure additionally provides health checks, automatic recovery of failed instances, and resource scaling based on system demand.