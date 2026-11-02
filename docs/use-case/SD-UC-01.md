# Sequence Diagram: SD-UC-01 Reserve a seat

> Worked example for teaching (LabDesk). Not a student submission and not a real product.

Lesson 4, analysis level: how the parts of LabDesk talk to each other when a student reserves a
seat. The lifelines are the elements of the [physical design](../architecture/architecture.md).
The student's choices (which slot, which seat) are shown in the activity diagram
[AD-UC-01](../activity/AD-UC-01.md), not here.

| Field | Value |
|---|---|
| Use case | UC-01 Reserve a seat |
| Version | v2 (split from "Booking flow", which told UC-01 and UC-02 together) |
| FRs | FR-01-01 to FR-01-06 |

```mermaid
sequenceDiagram
  actor S as Student
  participant W as Web app
  participant B as Booking service
  participant D as LabDesk database
  participant N as Notification adapter
  participant M as Email service
  S->>W: open booking page
  W->>B: list slots (next 7 days)
  B->>D: read slots and free-seat counts
  D-->>B: slots
  B-->>W: slots with free seats
  S->>W: choose slot, choose seat, confirm
  W->>B: create booking(student, slot, seat)
  B->>D: read bookings of student in slot
  alt student already holds a booking in this slot
    B-->>W: rejected: existing booking (FR-01-05)
  else seat booked by someone else since the map loaded
    B->>D: re-check seat inside the save transaction
    B-->>W: rejected: seat taken (FR-01-04)
  else seat still free
    B->>D: save booking [Confirmed]
    B->>N: booking confirmed
    N->>M: send confirmation with check-in QR (FR-01-06)
    B-->>W: booking confirmed
  end
  W-->>S: result
```

The `alt` fragments here are outcomes decided inside the system, so they belong in a sequence
diagram. A choice the student makes would be a decision in the activity diagram instead.
