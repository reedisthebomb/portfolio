# Step Companion

**One line:** Native Android prototype for structured, sponsor-supported personal development work.

## Overview

A native Android application prototype supporting a structured, guided 12-step workflow with a sponsor-review model layered on top — private by default, with explicit user-controlled sharing states rather than always-on visibility.

## Engineering highlights

- Guided multi-stage workspaces (Steps 1–12) built from original prompt content.
- Explicit sponsor-sharing state machine: private → ready for sponsor → needs discussion → resolved — a real state-machine design, not just a boolean "shared" flag.
- Structured data capture for specific workflows (e.g., categorized inventory sections; a dedicated amends-planning flow with sponsor-review language).
- Voice-to-text input integrated into major writing fields for faster capture.
- Local-first persistence via Android shared preferences — no data leaves the device by default.

## Stack

Native Android (Kotlin/Java), Android SharedPreferences, on-device voice-to-text.

## Status

Prototype.

## Repository

Private — [github.com/reedisthebomb/recovery-step-companion](https://github.com/reedisthebomb/recovery-step-companion)
