# Sequence Diagram: SD-UC-04 Check in at the lab

> Worked example for teaching (LabDesk). Not a student submission and not a real product.

Lesson 4, analysis level. The student scans the QR code on the lab door with the phone camera; the
link opens LabDesk in the phone browser.

| Field | Value |
|---|---|
| Use case | UC-04 Check in at the lab |
| Version | v1 |
| FRs | FR-02-01, FR-02-02, FR-02-03 |

```mermaid
sequenceDiagram
  actor S as Student
  participant W as Web app
  participant C as Check-in service
  participant D as LabDesk database
  S->>W: open check-in link (lab, slot)
  W->>C: check in(student, lab, now)
  C->>D: read Confirmed booking of student for lab and current slot
  D-->>C: booking or none
  alt more than 15 minutes after the slot started
    C-->>W: refused: seat released (FR-02-03)
  else no Confirmed booking
    C->>D: read the student's bookings of today
    C-->>W: failed, with today's bookings (FR-02-02)
  else Confirmed booking found
    C->>D: set booking [Checked-in]
    C-->>W: checked in (FR-02-01)
  end
  W-->>S: check-in result
```
