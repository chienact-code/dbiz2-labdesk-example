# UI Conventions: LabDesk (worked example)

> Worked example for teaching. Not a student submission and not a real product.

## 1. Language and tone

- Interface language: English by default, Vietnamese available in settings. Every message below
  has both versions in the translation file.
- Address the user as "you" (Vietnamese: "bạn").
- Button labels are verbs that say what happens: "Book seat", "Cancel booking". Never "OK" or
  "Submit".

## 2. Formats

| Item | Format | Example |
|---|---|---|
| Date | dd/MM/yyyy | 16/10/2026 |
| Time | HH:mm, 24-hour | 09:00 |
| Slot | HH:mm–HH:mm | 09:00–11:00 |
| Seat code | Room letter + two digits | B-07 |
| Room | "Room" + letter | Room B |

## 3. Components

| Component | When to use | Notes |
|---|---|---|
| Primary button | the one main action of a screen | one per screen, full width on mobile |
| Secondary button | alternative actions | outline style |
| Seat tile | one seat on the seat map | state shown by colour AND an icon or letter |
| Banner | non-blocking information | e.g. "Booking closes when the slot starts" |
| Modal | confirm or cancel a single action | never used for navigation |
| Toast | short confirmation after success | disappears after 4 seconds |

## 4. Messages

| Situation | Pattern | Example |
|---|---|---|
| Seat taken (FR-01-04) | what happened + what to do | "Seat B-07 was just booked by someone else. Please choose another seat." |
| Already booked (FR-01-05) | what exists + link | "You already have seat B-03 in this slot. View my bookings." |
| Empty slot list | why + next action | "No free slots in the next 7 days. Try another room." |
| Network error | what happened + retry | "Not saved yet. Check your connection and try again." |

## 5. Accessibility minimums

- Body text contrast at least 4.5:1 (WCAG 2.2, 1.4.3).
- Seat states never shown by colour alone (WCAG 2.2, 1.4.1): free, booked and blocked seats also
  differ by icon.
- Seat tiles at least 24 by 24 CSS pixels (WCAG 2.2, 2.5.8).
- Smallest supported width: 360px.
