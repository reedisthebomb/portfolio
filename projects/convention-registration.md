# Convention Registration Desk

**One line:** Full-stack event registration and operations platform — payments, badge printing, check-in, and financial reconciliation for a multi-day convention.

## Overview

A private, full-stack control center built to run the registration desk for a multi-day in-person convention: walk-up and pre-registration, payment processing, badge printing, check-in, merchandise, scholarships, cash reconciliation, and reporting. Deliberately architected as a separate system from the public-facing event information website, keeping operational/financial data isolated from public content.

## Engineering highlights

- Relational database with staff authentication, role-based access control (RBAC), and full audit logging.
- Dual-path payment handling: cash sessions with reconciliation, and Square Terminal integration (sandbox-tested payment boundary).
- Automated badge generation: six-position Avery 5392 front-only PDF layout with partial-position selection and print-run recording.
- External intake pipeline from Jotform (raw intake capture, import boundary, order reconciliation) instead of manual data entry.
- Emergency CSV export as a resilience fallback if the system needs to be bypassed on-site.
- End-to-end test coverage: unit tests (Vitest) and browser-driven e2e tests (Playwright).

## Stack

TypeScript, Vite + React, Express-style Node server (`tsx`), libSQL/SQLite, Playwright, Vitest, Jotform API, Square Terminal API.

## Status

Built for and used at a real event; companion project `convention-status-viewer` provides a lightweight public status page.

## Repository

Private — [github.com/reedisthebomb/convention-registration](https://github.com/reedisthebomb/convention-registration)
