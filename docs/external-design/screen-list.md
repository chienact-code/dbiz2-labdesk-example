# Screen List: LabDesk (worked example)

> Worked example for teaching. Not a student submission and not a real product.

Screen ID pattern: `S-<feature>-<nn>`. Shared screens use `S-F00-<nn>`.

| Screen ID | Screen name | Actor | Feature | Shown when (purpose) | Entry points | Use cases / FRs served | Priority | Screen spec |
|---|---|---|---|---|---|---|---|---|
| S-F00-01 | Sign in | Student, Lab Technician | F-00 | First visit, or session expired | Any link while signed out | (platform) | Must | `screens/screen-spec-S-F00-01.md` |
| S-F01-01 | Slot picker | Student | F-01 | Student wants to book: labs and slots of the next 7 days with free-seat counts | Home after sign in; "Book another" in S-F01-03 | UC-01 · FR-01-01 | Must | `screens/screen-spec-S-F01-01.md` |
| S-F01-02 | Seat map | Student | F-01 | Student picked a slot and chooses a seat | S-F01-01 | UC-01 · FR-01-02, FR-01-03, FR-01-04, FR-01-05 | Must | `screens/screen-spec-S-F01-02.md` |
| S-F01-03 | My bookings | Student | F-01 | Student checks, cancels or opens the QR of a booking | Menu; success state of S-F01-02; link in email | UC-02, UC-03 · FR-01-07 | Must | `screens/screen-spec-S-F01-03.md` |
| S-F02-01 | Check-in result | Student | F-02 | Student scanned the lab door QR code | Phone camera opens the check-in link | UC-04 · FR-02-01, FR-02-02, FR-02-03 | Must | `screens/screen-spec-S-F02-01.md` |
| S-F03-01 | Lab occupancy | Lab Technician | F-03 | Technician watches today's slots and check-ins | Home after sign in (technician) | UC-07 | Should | `screens/screen-spec-S-F03-01.md` |
| S-F03-02 | Seat maintenance | Lab Technician | F-03 | Technician blocks or unblocks seats | S-F03-01 | UC-06 | Should | `screens/screen-spec-S-F03-02.md` |

## Modals and overlays

| Modal | Opened from screen | Purpose |
|---|---|---|
| Cancel booking? | S-F01-03 | Confirm cancellation of one booking |
| Block seat | S-F03-02 | Enter reason and period for blocking a seat |

## What is deliberately not a screen

| Candidate | Why it is not a screen |
|---|---|
| "Booking success" | Success state of S-F01-02 |
| "Seat already taken" | Error state of S-F01-02 (FR-01-04) |
| "Check-in failed" | Error state of S-F02-01 |
| Release no-show seats (UC-05) | Time-triggered, no user interface; the student only receives an email |
