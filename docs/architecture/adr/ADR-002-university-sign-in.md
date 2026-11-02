# ADR-002: Sign in with the university account

> Worked example for teaching (LabDesk). Not a student submission and not a real product.

| Field | Value |
|---|---|
| Status | Accepted |
| Date | Lesson 4 |

**Context.** Every student and technician already has a university account. A separate LabDesk
password would mean a registration flow, password resets and a store of credentials.

**Decision.** Users sign in through the university sign-in service. LabDesk reads the identity and
the role (student or staff) and keeps no passwords.

**Consequences.** No registration use case. "University accounts" is an EIF in W0 Table 4.
FR-00-01 carries an INT work item for the integration, and FR-00-02 enforces the roles.
