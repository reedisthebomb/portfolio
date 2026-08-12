# Home Assistant Agent

**One line:** CLI automation agent for building and safely operating a real Home Assistant deployment.

## Overview

A durable local workspace and CLI agent for managing a home's Home Assistant instance — dashboards, automations, scripts, and camera/display integrations — with a design that separates read-only diagnostics from state-changing actions.

## Engineering highlights

- Unauthenticated health checks for the Home Assistant UI and Observer (safe to run anytime, no credentials required).
- Authenticated REST reads for config, states, services, events, and entity lookup.
- Guarded service calls that require an explicit `--yes` confirmation flag, preventing accidental state changes to real home devices.
- Intended as the long-term basis for larger Home Assistant build/change work, not a one-off script.

## Stack

CLI agent, Home Assistant REST API, service orchestration.

## Status

Active, in use managing a real home network.

## Repository

Private — [github.com/reedisthebomb/home-assistant-agent](https://github.com/reedisthebomb/home-assistant-agent)
