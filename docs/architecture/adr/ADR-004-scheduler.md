# ADR-004: Add a scheduler for timed jobs

> Worked example for teaching (LabDesk). Not a student submission and not a real product.

| Field | Value |
|---|---|
| Status | Accepted |
| Date | Lesson 7 |

**Context.** Drawing the activity diagram AD-UC-05 showed that no-show seats must be released 15
minutes after each slot starts, with nobody clicking anything. The Lesson 4 architecture had no
element that starts work on its own.

**Decision.** Add a Scheduler in the business layer. It starts the no-show release for each slot,
and later timed jobs such as the reminder email (FR-01-09).

**Consequences.** Architecture moves to v2. W1 gains the hidden work item "Scheduler set-up for
timed jobs" under FR-02-04. The finding is closed in the Inputs check table of
[activity-index](../../activity/activity-index.md) (row 3).
