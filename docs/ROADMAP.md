# RentWise implementation plan

## First milestone

Design a single-business workflow using fictional data. Create workspace, staff membership, equipment category, equipment unit, customer, reservation, and reservation-unit records.

Acceptance criteria:

- Every business-owned record belongs to a workspace.
- Staff can read and change only records in their own workspace.
- Equipment units have a clear condition and availability state.

## Second milestone

Implement inventory CRUD, date-range availability, and reservations. Enforce conflict prevention in the database, including concurrent requests.

Acceptance criteria:

- Adjacent half-open bookings are allowed unless a turnaround buffer applies.
- Overlapping confirmed bookings for the same unit are rejected atomically.
- Cancelling a reservation releases the unit.
- Tests cover invalid dates, conflicts, cancellation, and concurrent requests.

## Third milestone

Add manual deposit status, pickup and return records, damage notes, and overdue indicators. Test complete staff workflows in Playwright.

## Fourth milestone

Deploy a demo with fictional equipment and customers. Add screenshots and the real demo URL to the README. Ask prospective rental businesses for feedback without claiming any existing customers or interview relationships.
