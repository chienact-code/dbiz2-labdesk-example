# ADR-001: One web app for every user

> Worked example for teaching (LabDesk). Not a student submission and not a real product.

| Field | Value |
|---|---|
| Status | Accepted |
| Date | Lesson 4 |

**Context.** Students book from their phones and from lab computers; technicians work on lab
computers. Check-in starts from a QR code scanned with the phone camera.

**Decision.** Build one responsive web app that serves both students and technicians. No native
mobile app in this release.

**Consequences.** The QR check-in link opens in the phone browser. The native app is recorded as
Won't-have in W0 Table 3. One code base keeps DBIZ3 within team capacity.
