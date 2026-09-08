# Absolute Beauty — Salon Operations Dashboard

**One line:** Private operations dashboard for a working salon — scheduling, client history, service pricing, retail inventory, and a full expense/receipt tax organizer, all on honest server-backed state.

## Overview

A full business operations dashboard built for a real, operating salon, replacing paper and spreadsheets with one persistent, server-backed system for the day-to-day: booking and rescheduling, client notes and rebooking, menu pricing, retail/backbar inventory, and year-round tax-document organization. Built deliberately as a private single-owner tool with salon-native language throughout (services, formulas, color bar, backbar, deposits, no-shows) rather than generic SaaS framing.

## Engineering highlights

- **Honest data model, enforced.** Appointments, services, clients, inventory, expenses, and settings all persist server-side through an atomic write-and-rename JSON store with in-process write serialization; a hosted SQL backend implements the same update API as an alternate deployment path. No demo or sample data anywhere — automated tests assert the server-rendered HTML never shows fabricated clients, sales, or a false "integration connected" state.
- **Pricing calculator.** Derives a target hourly rate from the owner's monthly revenue goal, fixed costs, and bookable hours, then pre-fills service and appointment prices from duration plus product cost — while always staying hand-editable, backing off the moment the owner types her own number. Side-by-side national vs. regional price benchmarks for services, and keystone-markup retail suggestions for inventory.
- **Receipt capture and tax organization.** On-device receipt OCR (Tesseract WASM) with a real image-preprocessing pass — grayscale, percentile contrast stretch, adaptive upscaling, dual page-segmentation passes — auto-fills vendor, date, amount, and category. Expenses map to Schedule-C categories with plain-language deductibility guidance; a one-click export builds a real multi-sheet `.xlsx` and a single "tax package" zip (spreadsheet plus every receipt photo, foldered by category) for handoff to a preparer.
- **Read-only calendar overlay.** Imports the owner's personal calendar from a private iCalendar (ICS) URL — recurring-event expansion, 15-minute caching, and an honest "couldn't reach that link" failure state rather than a fabricated one — chosen deliberately over full calendar OAuth to avoid a provider-side app-verification dependency.
- **Real mobile client.** Audited pass for iOS Safari: `viewport-fit` / safe-area insets, `svh`/`dvh` viewport units, 44px minimum tap targets, input-zoom guards, and an installable PWA with hand-generated icons. Several framework viewport/manifest bugs were found and worked around at the server layer.
- **Auth and recovery.** Username/password gate with 30-day stateless HMAC-signed sessions and a password-recovery flow; private-network exposure over Tailscale HTTPS.
- **Square integration** is scoped as a five-phase plan (OAuth → read-only booking sync → in-app scheduling → Web Payments checkout → webhooks); until it is built the UI honestly shows "not connected" instead of faking readiness.

## Stack

React 19, TypeScript, [vinext](https://www.npmjs.com/package/vinext), atomic JSON persistence (hosted libSQL/D1 as an alternate backend), Tesseract.js, JSZip, `node-ical`, Playwright, systemd, Tailscale.

## Status

Live, in daily use by the business, deployed as a systemd service on a self-hosted server.

## Repository

Private — `github.com/reedisthebomb/absolute-beauty`
