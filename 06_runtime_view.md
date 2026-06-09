# Runtime View

This runtime view documents two failure scenarios that are important for the architecture:

1. a grade notification cannot be delivered immediately;
2. the result of a payment request is lost during communication with the external FMS.

The scenarios use building blocks from the Building Block View. The Message Queue and the background workers are technical runtime elements that support these building blocks.

## Mapping to Building Blocks

| Runtime Participant | Type | Responsibility |
|---|---|---|
| Authentication | Building block | Verifies user identity and permissions |
| Grades Management | Building block | Validates and stores grades |
| Grades Collection | Data storage | Stores grade records |
| Notification Worker | Runtime component | Processes grade notifications |
| Message Queue | Infrastructure | Retains notification messages |
| Billing & Payments | Building block | Manages payment requests and status |
| Payments Collection | Data storage | Stores payment records and status |
| Payment Verification Job | Runtime component | Checks unresolved payments |
| FMS | External system | Processes payments and returns their status |

The MongoDB collections follow the data ownership principle from section 8.4. Grade data is handled by Grades Management and payment data by Billing & Payments.

## 6.1 Grade Notification Cannot Be Delivered

### Initial Situation

A lecturer publishes grades for a course. Grades Management stores the grades and informs the students that new grades are available.

The email connection may be unavailable after the grades have already been stored. Repeating the complete grade submission would be wrong because the grade data is already correct.

![Grade Publication Runtime Scenario](images/runtimeview_gradepublication.png)
*Figure 6.1: Grade publication with delayed notification*

### Runtime Steps

1. `Authentication` verifies that the lecturer may publish grades for the course.
2. `Grades management` validates and stores the grades.
3. If storage fails, no notification is created and the lecturer receives an error.
4. After successful storage, `Grades management` adds a notification to the Message Queue.
5. The lecturer is informed that the grades were published and the notification was scheduled.
6. If delivery fails, the Notification Worker retries the queued message later.

### Architectural Decision

Grade storage and notification delivery are separated. Grades Management is responsible for the grade data, while the Message Queue ensures that a temporary email failure does not lose the notification.

The response to the lecturer means:

> The grades were stored and the notification was scheduled.

It does not mean that every student has already received an email.

### Expected Result

- A failed grade update creates no notification.
- Stored grades remain available if email delivery fails.
- The notification is retried without storing the grades again.
- A failure of the email connection does not block Grades Management.

---

## 6.2 Payment Result Is Unknown

### Initial Situation

A student starts a payment. Billing & Payments stores the operation and sends a request to the external Financial Management System.

The FMS may process the payment, but the network connection can fail before its response reaches the UMS. The UMS then does not know whether the payment succeeded.

![Payment Runtime Scenario](images/runtimeview_paymentprocessing.png)
*Figure 6.2: Payment processing with a lost FMS response*

### Runtime Steps

1. `Authentication` verifies the student.
2. `Billing & payments` stores the payment as `PENDING` with a unique request ID.
3. If the payment cannot be stored, the operation stops and no request is sent to the FMS.
4. After successful storage, the payment request is sent to the FMS.
5. A normal FMS response changes the status to `CONFIRMED` or `FAILED`.
6. If the response is lost, the payment remains `PENDING` and the student is informed that it is being verified.
7. The Payment Verification Job later asks the FMS for the status of the existing request.
8. The job stores `CONFIRMED` or `FAILED`. If the FMS is still unavailable, it keeps `PENDING` and tries again later.
9. The student can request and view the current payment status.

### Architectural Decision and CAP

CAP is not the main concern between the internal modules of the modular monolith. It is relevant at the network boundary between the UMS and the independently deployed FMS.

During a network failure, the UMS cannot provide both an immediate final response and guaranteed correct payment information. Billing & Payments therefore prioritizes consistency:

- it does not display an unconfirmed payment as successful;
- it keeps the payment in a controlled `PENDING` state;
- it checks the existing payment later using the same request ID instead of creating a second payment.

### Expected Result

- An unknown payment result is never shown as successful.
- The payment is not submitted a second time.
- The student sees the clear temporary status `PENDING`.
- The result eventually becomes `CONFIRMED` or `FAILED`.
- If the FMS remains unavailable, the payment stays `PENDING` and is checked again later.

## Summary

| Scenario | Actual Risk | Responsible Building Block | Architectural Response |
|---|---|---|---|
| Grade notification | Grades are stored, but notification delivery fails | Grades management | Message Queue retains the notification for a later retry |
| Payment processing | The FMS response is lost and the payment result is unknown | Billing & payments | Store `PENDING` and retrieve the existing payment status later |
