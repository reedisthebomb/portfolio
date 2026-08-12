# Recovery Sponsor Hub

**One line:** An AI-backed AA/NA support tool — chat, meeting-topic generation, and sharing-point suggestions grounded in program literature.

## Overview

A small web app that puts a "virtual sponsor" persona in reach: an ongoing chat for AA/NA questions, meeting-topic generation (phrased as statements, never questions), and sharing-point suggestions in multiple tones. Answers are grounded in the actual source literature — the Big Book of Alcoholics Anonymous for AA questions, the Narcotics Anonymous Basic Text for NA questions — rather than generic LLM output. Explicitly scoped as a support tool, not a replacement for a real sponsor, fellowship, doctor, or crisis line.

## Engineering highlights

- Integrates with [Claude Relay](claude-relay.md) for AI calls — no Anthropic API key held by this app, and no per-token billing exposure.
- Persona and prompt design grounded in specific program texts rather than open-ended generation.
- Deliberately simple frontend (static HTML/CSS/JS, no build step) served directly by the Express backend — no unnecessary complexity for what the app needs to do.

## Stack

Node.js, Express, static HTML/CSS/JS frontend, Claude Relay for AI access.

## Status

Live.

## Repository

Private — [github.com/reedisthebomb/Recovery.ahent.12step](https://github.com/reedisthebomb/Recovery.ahent.12step)
