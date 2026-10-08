# Tech It Easy — Business Website + Operations Platform

**One line:** The public website, customer-facing request funnel, and internal operations system for a one-person South Arkansas technology business — one deployable app, with an automation layer and optional on-premises AI.

## Overview

A single Next.js application that covers both sides of running a small technology service business. The public side is a marketing site with a service-request funnel and interactive "see what's possible" demos. Behind a login sits **Tech It Easy OS**: leads, customers, service tickets, projects, estimates, equipment records, files and photos, follow-ups, a calendar, reports, and a knowledge base. A lead submitted on the website shows up in the OS, converts to a customer in one click, becomes a ticket, and ends in a printable service report — the whole job lifecycle in one system, with an activity timeline on every record.

It was deliberately built as one app, one database, and one deploy (rather than a monorepo of services) because the owner is a single person: fewer moving parts, still cleanly separated by route group.

## Engineering highlights

- **Full job lifecycle, tested end to end.** Website request (with photo upload) → lead → customer → location → ticket → notes/photos → completion → follow-up → service report (internal notes never shown to the customer) → estimate sent → accepted → project. A Playwright test drives this entire path against the production Docker stack.
- **Own auth, small surface.** scrypt password hashing, random 256-bit session tokens stored only as SHA-256 hashes, httpOnly/SameSite cookies, Postgres-backed rate limiting (per IP and per account), an audit log, and `requireUser()` on every server action. Public forms add Zod validation and a honeypot.
- **Event outbox + automation.** Every domain event (lead created, ticket completed, estimate accepted…) is recorded and sent as an HMAC-signed webhook to **n8n**, which runs the hourly appointment-reminder and morning-digest workflows by calling bearer-protected app endpoints. A failed webhook never blocks the user and stays visible in a log. All customer-facing messages are opt-in and off by default.
- **Customer estimate approval link.** An unguessable per-estimate URL lets a customer review and approve or decline once; approval creates the project exactly like an in-app acceptance. Drafts, expired estimates, and bad tokens are not answerable.
- **Optional, private AI.** A provider abstraction (off by default, or a local Ollama model) drafts lead summaries, ticket notes, and handoff summaries. Prompts are scrubbed of secrets, credential references are never sent, and output is only ever a draft saved by an explicit click.
- **Hand-built motion and illustration.** Each service page has an animated hero illustration drawn as inline SVG in the brand's circuit-trace style (a smart-home cutaway, a 24-function office network, a service-area radar, and more), plus a scroll/page-transition motion layer — with zero animation dependencies, server-rendered, decorative-only for screen readers, and fully honoring `prefers-reduced-motion`.
- **Accessibility and phone-first checks in CI-style tests.** axe (WCAG 2A/AA) scans, a no-horizontal-scroll check on every public page at phone width, and a regression test for the header menus.
- **Operations done properly.** Docker Compose stack (app, PostgreSQL 17, n8n, Caddy, optional Ollama), tailnet HTTPS, health endpoint, backup and restore scripts that were exercised with row-count verification and a full restore, and persistence verified across a full stack restart. A pinned n8n version with the reason recorded in the decisions log.

## Stack

Next.js 16, React 19, TypeScript, PostgreSQL 17, Drizzle ORM (versioned SQL migrations), Zod, n8n, Caddy, Docker Compose, Ollama (optional), Tailwind CSS, Vitest, Playwright + axe-core, Tailscale.

## Status

Live and in use on a self-hosted server over private HTTPS. Public-domain launch and real email delivery are the next planned steps; a full customer portal is on the roadmap (the estimate approval link is its first slice).

## Repository

Private — `github.com/reedisthebomb/tech-it-easy`
