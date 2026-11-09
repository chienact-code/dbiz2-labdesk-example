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

## 6. Design tokens

Every LabDesk mockup uses only these values. The wireframes are drawn at 360px and exported at
3x, so every image in `screens/img/` is 1080 pixels wide.

| Token | Value | Used for |
|---|---|---|
| colour/primary | #0F766E | primary button, selected seat, links, success check mark |
| colour/text | #1F2933 | titles |
| colour/text-body | #3F4A54 | banner, legend, seat codes, summary line |
| colour/text-muted | #5B6670 | slot line, hints, booked and blocked seat marks |
| colour/border | #848E97 | free seat tile, Back button |
| colour/border-light | #D5DBDF | banner and card borders, booked seat fill |
| colour/surface | #F4F6F7 | banner background |
| colour/blocked-hatch | #E5E9EC | stripes of a blocked seat |
| colour/skeleton | #EEF1F3 | loading placeholders |
| colour/disabled | #C5CDD3 | disabled primary button, seat grid outline |
| colour/error-border | #B45309 | error message border |
| colour/error-text | #7C3A06 | error message text |
| colour/error-bg | #FDF3E3 | error message background |
| font/family | Lato, fallback Calibri, Arial | all text |
| font/size | title 19px, body 13px, small 11px, button 15px | |
| space/unit | 4px; screen padding 16px, grid gap 8px | padding, gaps |
| radius | primary button 10px, banner and card 8px, seat tile 7px | corners |
| frame/width | 360px | every mockup is drawn at this width |

Contrast, checked with the WCAG 2.2 formula:

| Pair | Ratio | Needed |
|---|---|---|
| text #1F2933 on white | 14.8:1 | 4.5:1 (1.4.3) |
| text-muted #5B6670 on white | 5.9:1 | 4.5:1 (1.4.3) |
| white on primary #0F766E | 5.5:1 | 4.5:1 (1.4.3) |
| error-text #7C3A06 on error-bg #FDF3E3 | 7.8:1 | 4.5:1 (1.4.3) |
| border #848E97 on white (seat tile edge) | 3.3:1 | 3:1 (1.4.11) |

The disabled button (white on #C5CDD3) is exempt: WCAG 1.4.3 does not apply to inactive
components. The blue numbered circles on `*-numbered.png` images are notes for readers, not part
of the product, so they are not a token.
