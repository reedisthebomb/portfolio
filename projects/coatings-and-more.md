# Coatings & More — Estimates & Invoices

**One line:** Private, installable estimate-and-invoice app for a small painting contractor — exact pricing math, branded PDFs, and phone-first design for a non-technical owner.

## Overview

A full-stack progressive web app built for a real small business. The owner builds a quote in three plain-English steps (Customer → Work & price → Review), then shares a PDF through his phone's own mail or messages. Installable on a phone's home screen, it runs on shared self-hosted infrastructure alongside other production apps, with its own isolated service, data, and backups.

## Engineering highlights

- **Exact money handling.** Prices are stored as integer cents with decimal arithmetic; line totals round once, half-up. Pricing works forward (area × rate) and backward (a target total derives the per-square-foot rate while preserving the exact cents). Rounding, tax and discount order, and zero/negative/invalid inputs are covered by unit tests.
- **Alternative options that never sum.** One quote can hold independent options (for example, two ways to refinish a deck). Each option has its own total, and an invoice copy must be made from exactly one option.
- **Immutable history.** Every document stores its own customer, address, business, and terms snapshot. Each PDF export is a fixed per-revision record, and customer-facing templates are versioned: when a signature/authorization block was added to every estimate and invoice, earlier exports and shared links kept their original layout. Saves use revision checks, so two devices can't silently overwrite each other.
- **Server-rendered PDFs.** One shared HTML template drives the on-screen preview, print, the PDF (headless Chromium via Playwright), and the customer view page, so they can't drift apart. PDF jobs run one at a time with a timeout and a bounded queue. Output has repeating table headers, controlled page breaks, long-description continuation markers, page numbers, and a printed customer-authorization block that is kept together on one page.
- **Security.** Two roles enforced on the server (business owner, site administrator), scrypt password hashing, forced password change on first login, HttpOnly/Secure/SameSite=Strict cookie sessions, CSRF tokens, login throttling, revocable random share-link tokens, and validated image uploads (decoded, re-encoded, no SVG).
- **Idempotent data import.** Historical records are brought in through a transactional, source-keyed import that is safe to re-run, preserves later edits, and reports mismatches instead of overwriting. Unknown facts (original dates, quote numbers, acceptance) stay explicitly blank rather than being invented, and import-only reference numbers are never printed on customer documents.
- **Installable PWA.** Web manifest with maskable icons, a service worker that caches only hashed app assets (never customer data or PDFs), and versioned icon URLs so a stale favicon can't stick. The brand mark is original SVG artwork rendered to every required size by a script.
- **Operations.** A systemd service with memory and CPU limits on a shared host, release-based deploys with one-command rollback and before/after health checks of the neighbouring apps, nightly SQLite-consistent backups with an off-host copy, a restore procedure rehearsed on the real server, and a read-only diagnostic command that renders stored documents to PDF on the production host without touching data.
- **Verification.** 82 unit and API tests plus automated browser runs (about 100 checks) covering the full first-login → quote → PDF → invoice workflow, import idempotency, no-horizontal-scroll layout at six screen widths, dark mode, and a guard that no logo or placeholder artwork leaks onto customer documents. PDFs were inspected page by page, including a 6-page stress document.

## Stack

TypeScript, React, Vite, Node.js, Fastify, SQLite (better-sqlite3), decimal.js, sharp, Playwright/Chromium, systemd, Caddy.

## Status

Live and in use by the business.

## Repository

Private: `github.com/reedisthebomb/coatings-and-more`
