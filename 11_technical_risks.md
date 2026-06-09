# Risks and Technical Debts

This section describes the most important technical risks and debts that result from the chosen architecture.

The risks are based on the modular monolith, the integration with existing university systems, and the role-based access control described in the previous sections.

| ID | Risk / Technical Debt | Description and Possible Consequence | Mitigation |
|---|---|---|---|
| R-1 | Weak module boundaries | The modular monolith can become tightly coupled if modules directly access the logic or MongoDB collections of other modules. Changes in one business area could then affect unrelated parts of the system and make maintenance more difficult. | Define clear module responsibilities and collection ownership. Communication between modules should use their service interfaces. Module dependencies should be checked during code reviews. |
| R-2 | Dependency on SIS and FMS | The UMS depends on the external Student Information System and Financial Management System. These systems may be unavailable, respond slowly, or change their REST APIs. This could prevent student synchronization or leave payment operations unresolved. | Use documented API interfaces, timeouts, controlled error handling, and monitoring. Payment requests with an unknown result remain `PENDING` and are checked later instead of being repeated. |
| R-3 | Incorrect access permissions | Incorrectly defined roles or missing authorization checks could allow users to access or modify sensitive student, grade, attendance, or financial data. | Enforce RBAC in the backend for every protected endpoint. Add automated authorization tests for every role and log rejected access attempts. The frontend may hide unavailable functions, but it is not the security enforcement point. |

## Risk Priority

| Priority | Risk | Reason |
|---|---|---|
| High | Incorrect access permissions | Unauthorized access could expose or modify sensitive academic and financial data. |
| High | Dependency on SIS and FMS | External failures can directly affect important student and payment workflows. |
| Medium | Weak module boundaries | The impact increases over time as the system grows and more modules depend on each other. |
