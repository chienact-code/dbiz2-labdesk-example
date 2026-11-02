# ADR-003: Send email through an external email service

> Worked example for teaching (LabDesk). Not a student submission and not a real product.

| Field | Value |
|---|---|
| Status | Accepted |
| Date | Lesson 4 |

**Context.** LabDesk sends confirmations with a check-in QR code, no-show notices and seat-blocked
messages. Running a mail server is outside the team's skills and budget.

**Decision.** All email goes through an external email service, behind one Notification adapter.

**Consequences.** Email service is an external entity on the Context Diagram and a lane in the
activity diagrams. Its subscription is part of the running cost in W6. Email rows are INT work
items in W1.
