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
- Root-caused a silent resource leak on a fleet member (a stuck AI-agent service in an auth-failure retry loop, consuming ~42% CPU and 3GB RAM for weeks) by diffing host-level process data against container-level metrics — the leak was invisible to `docker stats` alone.
- Repurposed a spare ARM SBC (an Android TV box reflashed with a Debian-based Linux distro) into an independent uptime monitor and a redundant Tailscale subnet router, so network monitoring survives even if the primary server has problems — directly informed by the resource-leak incident above.
- Live camera NVR integration: ONVIF PTZ control and tuned dual-stream (record/detect) restreaming through go2rtc for pan-tilt IP cameras, with hardware-accelerated on-device object detection (no cloud dependency, no dedicated AI accelerator required).

## Stack

Docker Compose, containerized services, self-hosted, Tailscale-gated access.

## Status

Live, in continuous production use monitoring a real network.

## Repository

**Private — stays private.** [github.com/reedisthebomb/network-topology-agent](https://github.com/reedisthebomb/network-topology-agent) — unlike the rest of this portfolio, this repo is not slated to go public even after the portfolio does. Its `data/` folder holds live device inventory and raw network-scan output for a real, currently-running home network, so it's excluded from any future visibility flip by design.
