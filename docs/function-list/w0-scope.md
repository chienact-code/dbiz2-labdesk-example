# W0 Scope: LabDesk

> Worked example for teaching (LabDesk). Not a student submission and not a real product.

Lesson 5 (Function List workshop, block W0). Inputs: [CVCA](../context/cvca.md), [Context Diagram](../context/context-diagram.md), [Use Case Diagram](../use-case/use-case-diagram.md), all at v2.

## Table 1. Use case inventory

| Use case ID | Use case name | Primary actor | Assigned feature | Login required |
|---|---|---|---|---|
| UC-01 | Reserve a seat | Student | F-01 | Yes |
| UC-02 | Cancel a booking | Student | F-01 | Yes |
| UC-03 | View my bookings | Student | F-01 | Yes |
| UC-04 | Check in at the lab | Student | F-02 | Yes |
| UC-05 | Release no-show seats | Time (system-initiated) | F-02 | No |
| UC-06 | Block a seat for maintenance | Lab Technician | F-03 | Yes (technician) |
| UC-07 | View lab occupancy | Lab Technician | F-03 | Yes (technician) |

UC-05 was added after the Lesson 7 Inputs check (see [activity-index](../activity/activity-index.md), row 1).

## Table 2. Feature list (flows into W1)

| Feature ID | Feature name (business noun) | Scope in one sentence | Primary actors served | Owner | Use cases covered |
|---|---|---|---|---|---|
| F-00 | Platform and Access | Every user signs in with the university account, sees only what their role allows, and the service is deployed and watched. | Student, Lab Technician | Owner A (integrator) | none: precondition of every use case |
| F-01 | Seat Booking | Students find a free seat in a lab time slot, book it, see their bookings and cancel them. | Student | Owner B | UC-01, UC-02, UC-03 |
| F-02 | Check-in and No-show | Students confirm they came; seats nobody uses are given back and repeated no-shows are limited. | Student | Owner C | UC-04, UC-05 |
| F-03 | Lab Operations | Lab Technicians block faulty seats and watch how labs are used. | Lab Technician | Owner D | UC-06, UC-07 |

Feature count: 4 (allowed 3 to 6): PASS. Coverage against the CVCA: both primary actors (Student, Lab Technician) are served.

## Table 3. Won't-have (recorded, never dropped silently)

| Excluded from scope | How it surfaced | Reason for exclusion |
|---|---|---|
| Waiting list when a slot is full | Student survey in the user meeting | The faculty wants simple first-come booking for this release; revisit after one semester of data |
| Booking a whole lab for a class | Lecturer request in the user meeting | Class bookings already live in the faculty timetable; LabDesk only shows those slots as closed |
| Payment or deposits for seats | AI suggestion during W0 | Labs are free for students; a deposit would need the university finance office |
| Native mobile app | Team idea | The web app works on phones; the check-in QR opens in the phone browser |

## Table 4. Data functions

| Data group | ILF / EIF | Why | Function points |
|---|---|---|---|
| Labs, seats and time slots | ILF | LabDesk keeps the seat layout of each lab, the opening slots and the Blocked periods | 10 |
| Bookings | ILF | Created, cancelled, checked in and released by LabDesk | 10 |
| Booking rights | ILF | No-show count and suspension period per student (BR-04) | 10 |
| University accounts | EIF | Name, student or staff ID and role, read from the university sign-in service; never edited by LabDesk | 7 |
| **Total data-function points** | | | **37** |

The data group names are the names Screen Specs use as data sources (Lesson 8).

## Business rules

| BR | Rule |
|---|---|
| BR-01 | A student holds at most one booking per time slot. |
| BR-02 | Booking for a slot closes when the slot starts; check-in is open until 15 minutes after the start. |
| BR-03 | A blocked seat cannot be booked. |
| BR-04 | Three no-shows within 30 days suspend booking rights for 7 days. |
