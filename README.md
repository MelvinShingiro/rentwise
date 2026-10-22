# RentWise

![Status](https://img.shields.io/badge/status-planning-blue?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)
![Stack](https://img.shields.io/badge/stack-React%20%7C%20TypeScript%20%7C%20Supabase-3178C6?style=flat-square)

A general rental business management project for inventory, reservations, deposits, and returns.

**Status:** Repository setup and project planning. The application is not implemented yet. Features below describe the planned first release.

## About

RentWise will help a rental business keep track of what it owns, what is available, who has booked it, and when it should come back. It is intended for businesses renting equipment such as cameras, tools, sports gear, furniture, or event supplies.

The first release will support one business workspace, staff accounts, and individually tracked rental units. It will use fictional sample data and will not depend on any previous interview participants or customer relationships.

## Planned features

- Manage equipment categories, individual units, rental rates, and condition.
- Search availability over a requested date range.
- Create, confirm, and cancel reservations with customer contact records.
- Prevent overlapping confirmed bookings for the same rental unit.
- Track deposit amounts and statuses manually.
- Record pickups, returns, damage notes, and overdue rentals.
- Display a booking calendar and a simple availability dashboard.

## Planned tech stack

- **Frontend:** React, TypeScript, Vite, and Tailwind CSS.
- **Backend services:** Supabase Auth and PostgreSQL.
- **Booking logic:** PostgreSQL constraints and transactional functions, with frontend availability checks for feedback.
- **Testing:** Vitest for application logic, Playwright for browser workflows, and database tests for conflicting bookings and workspace access.
- **Deployment:** Cloudflare Pages for the frontend and Supabase Free for the database and authentication.

## Booking rules

Treat rental intervals as half-open ranges: a reservation covers its start time up to, but not including, its end time. Two bookings for the same unit conflict when `existing.start < new.end` and `new.start < existing.end`.

Enforce the no-overlap rule in PostgreSQL for confirmed reservations, so two simultaneous requests cannot both reserve the same unit. Cancelled bookings should release availability. Add turnaround buffers explicitly if the business needs time for inspections between rentals.

Every business-owned record will include a workspace identifier. Database row-level security and server-side checks will restrict staff access to their own workspace.

## Initial scope

The first release will record deposits and payments as statuses entered by staff. It will not process money, send paid SMS messages, or require a paid maps API. Expansion to multiple business workspaces can follow once the single-business workflow is tested.

## Roadmap

- [x] Create project documentation and contribution templates.
- [ ] Design the equipment, customer, booking, and rental-unit schema.
- [ ] Set up staff authentication and workspace access rules.
- [ ] Build inventory management and a booking calendar.
- [ ] Implement database-enforced reservation conflict checks.
- [ ] Add pickup, return, deposit, and overdue workflows.
- [ ] Add automated tests and fictional demo data.
- [ ] Deploy a public demo and document the results.

See the [implementation plan](docs/ROADMAP.md) and [deployment plan](docs/DEPLOYMENT.md).

## Getting started

```bash
git clone https://github.com/MelvinShingiro/rentwise.git
cd rentwise
```

This starter currently contains documentation and repository tooling. Application installation and run commands will be added alongside the first working implementation. The root `package.json` currently provides documentation tooling; React application scripts have not been added.

## Project structure

```text
.
├── .github/          # Issue forms, PR template, community files, labels
├── docs/
│   ├── DEPLOYMENT.md # Free hosting plan
│   ├── ROADMAP.md    # Build order and acceptance criteria
│   └── TEMPLATE.md   # Upstream template provenance
├── CHANGELOG.md
├── LICENSE
└── README.md
```

## Contributing

See the [contribution guide](.github/CONTRIBUTING.md), [code of conduct](.github/CODE_OF_CONDUCT.md), and [security policy](.github/SECURITY.md). Use the repository's issue forms for bugs, questions, and feature proposals.

## Maintainer

[Melvin Shingiro](https://github.com/MelvinShingiro).

## Template and license

Created from [bhdicaire/repository-template](https://github.com/bhdicaire/repository-template), with project-specific documentation and repository metadata. Original template guidance and screenshots remain under `docs/` as reference material.

[MIT License](LICENSE). The original template copyright notice is retained.
