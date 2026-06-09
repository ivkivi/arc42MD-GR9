# Architecture Constraints

## Technical Constraints

| Constraint                  | Explanation                                                                                  |
| --------------------------- | -------------------------------------------------------------------------------------------- |
| Frontend technology: React  | The frontend must be implemented using React.                                                |
| Backend technology: Node.js | Backend services must be implemented using Node.js.                                          |
| Database: MongoDB           | MongoDB must be used as the primary data store.                                              |
| Cloud hosting               | The application must be deployable on AWS.                                                   |
| Existing system integration | Integration with the Student Information System and Financial Management System is required. |
| Data protection compliance  | The system must comply with applicable privacy and data protection regulations.              |


## Organizational Constraints

| Constraint           | Explanation                                                                       |
| -------------------- | --------------------------------------------------------------------------------- |
| Multiple user groups | The system must support students, lecturers, administrators, and financial staff. |
| Web-based solution   | The application must be accessible through a standard web browser.                |
| Centralized platform | Academic, administrative, and financial processes shall be managed in one system. |


## Development Constraints

| Constraint                | Explanation                                                                         |
| ------------------------- | ----------------------------------------------------------------------------------- |
| Role-based access control | Authentication and authorization are mandatory.                                     |
| Modular architecture      | The system should be structured into independent functional modules.                |
| Scalability               | The architecture must support growing numbers of users and data.                    |
| Maintainability           | Future extensions should be possible with minimal impact on existing functionality. |

These constraints are reflected in the [Solution Strategy](04_solution_strategy.md), the [Building Block View](05_building_block_view.md), and the [Cross-cutting Concepts](08_concepts.md).

---

[← Previous: Introduction and Goals](01_introduction_and_goals.md) | [Overview](README.md) | [Next: Context and Scope →](03_context_and_scope.md)
