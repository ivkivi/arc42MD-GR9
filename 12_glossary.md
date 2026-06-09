# Glossary

This glossary defines the most important domain-specific and technical terms used in the architecture documentation.

| Term | Definition |
|---|---|
| UMS | University Management System. The web-based system documented in this project. |
| SIS | Student Information System. An existing external university system that provides official student master data and registration information. |
| FMS | Financial Management System. An existing external system that processes payments and provides financial transaction information. |
| Student Master Data | Official information about a student, such as student ID, name, study program, and registration status. |
| Enrollment | The process of registering a student for a course. |
| Grade Publication | The process in which a lecturer stores and releases grades so that students can view them. |
| Modular Monolith | An architecture in which the system is deployed as one application but internally divided into functional modules with clear responsibilities. |
| Building Block | A part of the system with a defined responsibility, such as Grades Management or Billing & Payments. |
| RBAC | Role-Based Access Control. Permissions are assigned based on roles such as Student, Lecturer, Administrator, and Finance Staff. |
| JWT | JSON Web Token. A signed token used by the backend to authenticate requests without storing server-side sessions. |
| Authentication | The process of verifying the identity of a user. |
| Authorization | The process of checking whether an authenticated user may access specific data or functionality. |
| API | Application Programming Interface. A defined interface through which software systems exchange data. |
| REST API | An HTTP-based interface used for communication between the frontend, backend, SIS, and FMS. |
| React | A JavaScript library used to implement the browser-based UMS frontend. |
| Node.js | A JavaScript runtime used to execute the UMS backend application. |
| HTTPS | An encrypted communication protocol used between web browsers, the UMS, and external REST APIs. |
| SMTP | Simple Mail Transfer Protocol. A protocol that can be used to send email notifications. |
| MongoDB | The database technology used as the central persistent data store of the UMS. |
| Collection | A group of related documents in MongoDB. Each UMS module manages the collections belonging to its business area. |
| Message Queue | A technical communication mechanism that temporarily stores messages until they can be processed. The UMS uses it for delayed grade notifications. |
| Notification | A message sent to a user about an event, such as the publication of a new grade. |
| PENDING | A temporary payment status indicating that the final result from the FMS is not yet known. |
| CONFIRMED | A payment status indicating that the FMS has confirmed the payment. |
| FAILED | A payment status indicating that the payment was rejected or could not be completed. |
| Request ID | A unique identifier used to recognize a payment request and prevent accidental duplicate processing. |
| CAP Theorem | A principle for distributed systems stating that during a network partition, a system cannot guarantee both full consistency and full availability. |
| Network Partition | A communication failure in which the UMS temporarily cannot reach an external system such as the FMS. |
| Data Ownership | The rule that each functional module manages its own data collections and other modules do not modify them directly. |
| Cloud Deployment | Operation of the UMS on AWS cloud infrastructure. |
| AWS | Amazon Web Services. The cloud platform used for hosting and operating the UMS. |
| CloudWatch | An AWS service used to collect logs, monitor the application, and trigger alerts. |
| CDN | Content Delivery Network. Infrastructure used to distribute the static React frontend efficiently. |
| Idempotent Request | A request that can be repeated using the same identifier without creating the same operation more than once. |

---

[← Previous: Risks and Technical Debts](11_technical_risks.md) | [Overview](README.md)
