# Fiber Locator Dashboard

**One line:** Cloud operations dashboard for fiber-optic locate work and Arkansas One Call ticket management.

## Overview

A production dashboard used to manage dig-ticket workflow for fiber-optic line locating. It ingests and reconciles data from multiple external systems — Outlook ticket exports, GeoCall printable pages and polygons, and Vetro fiber-network layers — into a single searchable, filterable view of active and historical dig tickets. Built around the reality of the job: field locators physically trace lines with a locate wand, so the dashboard is designed to support that workflow (ticket status, hiding/filtering, review state) rather than relying on GPS/map-accuracy shortcuts.

## Engineering highlights

- Multi-source data ingestion and reconciliation (Outlook exports, GeoCall, Vetro GIS layers) into one coherent record per ticket.
- Server-side persistence of a "Locator Default View" so operational state survives across sessions.
- Native Android companion app distributed through the Play Store (Android Auto compatibility required moving off sideloaded builds).
- Deployed and run continuously on a cloud server, not a local prototype.

## Stack

Node.js backend, server-rendered/React dashboard, cloud-hosted, companion native Android app.

## Status

Live, in active daily operational use.

## Repository

Private — [github.com/reedisthebomb/fiber.locator.dashboard](https://github.com/reedisthebomb/fiber.locator.dashboard)
