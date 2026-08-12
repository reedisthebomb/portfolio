# Network Topology Agent — NOC Dashboard

**One line:** Self-hosted network operations center (NOC) dashboard with live topology mapping, security triage, and automated health monitoring.

## Overview

A production NOC dashboard deployed via Docker Compose on a home/small-office server, accessible only to authorized clients over a private mesh network (Tailscale). It gives a real-time, evidence-labeled map of every device on the network alongside live gateway traffic, system health, and security triage — the kind of tooling normally associated with a small MSP or IT department, built and operated solo.

## Engineering highlights

- Docker Compose deployment with documented backup/restore and rollback procedures.
- Live topology map that labels devices by actual observed evidence rather than guesswork.
- Security triage view for surfacing anomalous devices/traffic.
- Bounded metrics/log storage (deliberate retention limits, not unbounded growth).
- Consolidated health-check script (`scripts/health-check.sh`) for one-command system verification.
- Full operator documentation (`docs/CORE_OPERATIONS.md`) covering access, updates, and recovery — written so the system is maintainable, not just functional.

## Stack

Docker Compose, containerized services, self-hosted, Tailscale-gated access.

## Status

Live, in continuous production use monitoring a real network.

## Repository

Private — available on request (not yet published to GitHub).
