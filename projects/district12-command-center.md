# District 12 Service Command Center

**One line:** Private records-and-finance platform for a regional service district's elected treasurer and secretary — double-checked money handling, budgets, minutes, an AI drafting assistant, and an audited, role-separated database.

## Overview

A full-stack web application built for the volunteer officers of a nonprofit service district and its annual convention. It gives the treasurer and secretary one shared, auditable record instead of scattered spreadsheets: a ledger, budgets, reconciliation against payment-processor exports, meeting minutes, calendars, and role-specific guides. Access is private to a closed network, and no member or financial data is published anywhere — this write-up describes the engineering only.

## Engineering highlights

- **Separation of duties in code.** Role-based access (administrator, treasurer, secretary, read-only) enforced on the server; separate District and Round-Up books that share bank accounts but are edited only by their own treasurer, with every change written to an audit log.
- **Ledger integrity.** Payment-processor transactions are imported and categorised, and multi-purpose payments are *split* so the parts always sum exactly to the original payment. Mark-cleared and void actions replace destructive edits.
- **Budget vs. actual.** Separate budgets per scope and year: proposed and approved amounts, the approving motion, spend-to-date, percent used, status flags, and a year-end pace projection — printable and phone-friendly.
- **Security and operations.** Password hashing, administrator-initiated resets that force a change and revoke open sessions, a security pass, nightly backups with an off-site copy, and one-command start / stop / backup / restore / update / doctor scripts.
- **AI assistant on its own runner.** A drafting/Q&A assistant with guarded access to the data; changes to finance data require re-authentication.
- **Documentation as a deliverable.** Architecture, governance, finance, security, privacy, backup/restore, importing, and trusted-servant handoff docs so the next officer can take over without the author.
- **Redesigned UI.** A custom theme and generated page art, checked visually at phone width.

## Stack

Next.js 16 (TypeScript, App Router), Drizzle ORM, PostgreSQL in Docker, systemd, Tailscale (tailnet-only access), Vitest.

## Status

Live and in use by the district officers (private network).

## Repository

Private — `github.com/reedisthebomb/district12-command-center`
