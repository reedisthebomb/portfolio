# Fiber Locator Dashboard

**One line:** Cloud operations dashboard for fiber-optic locate work and Arkansas One Call ticket management.

## Overview

A production dashboard used to manage dig-ticket workflow for fiber-optic line locating. It ingests and reconciles data from multiple external systems — Outlook ticket exports, GeoCall printable pages and polygons, and Vetro fiber-network layers — into a single searchable, filterable view of active and historical dig tickets. Built around the reality of the job: field locators physically trace lines with a locate wand, so the dashboard is designed to support that workflow (ticket status, hiding/filtering, review state) rather than relying on GPS/map-accuracy shortcuts.

## Engineering highlights

- Multi-source data ingestion and reconciliation (Outlook exports, GeoCall, Vetro GIS layers) into one coherent record per ticket.
- **Smart daily routing.** A rewritten route planner that honours real dispatch rules (day-based due dates, emergencies first, recall/second-request priorities, hidden/duplicate handling), inserts opportunistic stops by cheapest insertion, computes ETAs, flags overbooked or at-risk days, and rolls over after hours and weekends. Road-network routing runs on a self-hosted Valhalla instance (tiled, cached, time-budgeted, with a safe fallback). Ticket due dates are never altered by the planner.
- **Locate Overview and area history** views, covered by planner unit tests and Playwright smoke tests.
- Server-side persistence of a "Locator Default View" so operational state survives across sessions.
- Native Android companion app distributed through the Play Store (Android Auto compatibility required moving off sideloaded builds).
- Deployed and run continuously on a cloud server, not a local prototype.

## Stack

Node.js backend, server-rendered/React dashboard, cloud-hosted, companion native Android app.

## Status

Live, in active daily operational use.

## Repository

Private — `github.com/reedisthebomb/fiber.locator.dashboard`
