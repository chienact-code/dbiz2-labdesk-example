# LabDesk: worked example for DBIZ2 Lessons 7 and 8

Worked example used in DBIZ2 Digital Business Project II (VJCBI College, Foreign Trade University),
Lesson 7 (UML Activity Diagram) and Lesson 8 (External Design). It is a teaching example, not a
real product and not a student submission.

The folder layout is the one each team uses in its shared team folder in DBIZ2. In DBIZ3 the same
folders move into the team's GitHub repository unchanged.

## How to read this repository

Read in this order. Each file links to the previous one by ID (UC, FR, AD, Screen ID).

| Step | File | Lesson | What it shows |
|---|---|---|---|
| 1 | [`docs/activity/activity-index.md`](docs/activity/activity-index.md) | L7 | Inputs check against Lessons 3-4, and which use cases need an activity diagram |
| 2 | [`docs/activity/AD-UC-01.md`](docs/activity/AD-UC-01.md) | L7 | Activity diagram of a use case started by a student |
| 3 | [`docs/activity/AD-UC-05.md`](docs/activity/AD-UC-05.md) | L7 | Activity diagram of a use case started by time |
| 4 | [`docs/usage-flow.md`](docs/usage-flow.md) | L8 | One usage flow per actor, each step linked to its activity diagram and screens |
| 5 | [`docs/screen-list.md`](docs/screen-list.md) | L8 | Every screen, with states and modals kept apart |
| 6 | [`docs/screen-transition.md`](docs/screen-transition.md) | L8 | Screen transitions per actor |
| 7 | [`docs/ui-conventions.md`](docs/ui-conventions.md) | L8 | Conventions every screen follows |
| 8 | [`screens/screen-spec-S-F01-02.md`](screens/screen-spec-S-F01-02.md) | L8 | One complete Screen Spec, with its wireframe in `screens/img/` |

Only the files above are written out. The index and the screen list also name AD-UC-02, AD-UC-04,
AD-UC-06 and the other Screen Specs: they are left for students to write as practice.

Diagrams are Mermaid code blocks. The activity diagrams use `swimlane-beta`, which needs Mermaid
11.16 or later; if a diagram does not render in your viewer, paste the block into
[mermaid.live](https://mermaid.live).


LabDesk is a small computer-lab seat reservation system for a university faculty. It is the
running example in the DBIZ2 Function List workbook (Lesson 5 workshop) and is reused in
Lessons 7 and 8 so that students see one product move from function list to activity diagrams to
screens. It is a teaching example, not a real product and not a student submission.

## Actors and external systems

| Name | Kind | Notes |
|---|---|---|
| Student | Primary actor | Books, cancels and checks in |
| Lab Technician | Primary actor | Blocks seats, watches occupancy |
| Email service | External system | Sends confirmations and notices |
| Time | Trigger | Starts system-initiated activities (no-show release) |

## Features and use cases

| Feature | Name | Use cases |
|---|---|---|
| F-01 | Seat Booking | UC-01 Reserve a seat · UC-02 Cancel a booking · UC-03 View my bookings |
| F-02 | Check-in and No-show | UC-04 Check in at the lab · UC-05 Release no-show seats |
| F-03 | Lab Operations | UC-06 Block a seat for maintenance · UC-07 View lab occupancy |

## Functional requirements used in the examples (EARS)

| FR | Requirement |
|---|---|
| FR-01-01 | WHEN a student opens the booking page, the system SHALL display the labs and time slots of the next 7 days with the number of free seats in each. |
| FR-01-02 | WHEN a student selects a slot, the system SHALL display the seat map of that lab with each seat shown as free, booked or blocked. |
| FR-01-03 | WHEN a student confirms a free seat, the system SHALL save a booking for that student, slot and seat with status Confirmed. |
| FR-01-04 | IF the seat a student confirms was booked by someone else after the seat map was loaded, THEN the system SHALL reject the booking and reload the seat map with a message. |
| FR-01-05 | IF a student who already holds a booking in a slot confirms another seat in the same slot, THEN the system SHALL reject the booking and show the existing one. |
| FR-01-06 | WHEN a booking is confirmed, the system SHALL send the student a confirmation email that contains a check-in QR code. |
| FR-01-07 | WHEN a student cancels a Confirmed booking before its slot starts, the system SHALL set the booking to Cancelled and free the seat. |
| FR-02-01 | WHEN a student opens the check-in link of a lab between the start of a slot and 15 minutes after it, while holding a Confirmed booking for that lab and slot, the system SHALL set the booking to Checked-in. |
| FR-02-02 | IF a student opens the check-in link without a Confirmed booking for that lab and slot, THEN the system SHALL show why check-in failed and list the student's bookings for today. |
| FR-02-03 | IF a student opens the check-in link more than 15 minutes after the slot started, THEN the system SHALL refuse the check-in and say that the seat was released. |
| FR-02-04 | WHEN 15 minutes have passed since a slot started, the system SHALL set every booking of that slot that is still Confirmed to No-show and free its seat. |
| FR-02-05 | WHEN a booking becomes No-show, the system SHALL send the student a no-show notice. |
| FR-02-06 | IF a student reaches 3 no-shows within 30 days, THEN the system SHALL suspend the student's booking rights for 7 days. |

## Business rules

| BR | Rule |
|---|---|
| BR-01 | A student holds at most one booking per time slot. |
| BR-02 | Booking for a slot closes when the slot starts. |
| BR-03 | A blocked seat cannot be booked. |
| BR-04 | Three no-shows within 30 days suspend booking rights for 7 days. |

## Screens (Lesson 8)

| Screen ID | Name | Actor |
|---|---|---|
| S-F00-01 | Sign in | All |
| S-F01-01 | Slot picker | Student |
| S-F01-02 | Seat map | Student |
| S-F01-03 | My bookings | Student |
| S-F02-01 | Check-in result | Student |
| S-F03-01 | Lab occupancy | Lab Technician |
| S-F03-02 | Seat maintenance | Lab Technician |
