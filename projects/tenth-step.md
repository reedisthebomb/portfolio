# Tenth Step Companion

**One line:** Personal-development companion app with a full self-hosted voice pipeline — narrated audio content, speech-to-text, and forced audio/text alignment.

## Overview

A structured daily-practice companion application (web) built around a genuinely non-trivial audio/voice engineering stack: real narrated content generation, voice input instead of typing, and precise text-to-audio alignment for guided read-alongs — all running on self-hosted infrastructure rather than third-party voice APIs.

## Engineering highlights

- Self-hosted text-to-speech narration pipeline (Piper TTS, later Kokoro TTS with the `af_sky` voice) generating meditation/practice audio content — `content/generate_audio.py`.
- Self-hosted Whisper speech-to-text for a "no-type" voice interaction flow, replacing an earlier flaky browser `SpeechRecognition` implementation with a reliable server-side model.
- Forced audio/text alignment using `faster-whisper` to sync hand-recorded audio against reference text for a word-level "read along" feature (`generate_prayer_timings.py`), re-run per new audio upload.
- Admin-managed content model: editorial content (e.g. featured daily material) is managed through the app's own database/admin UI rather than scraped or hard-coded, with pin-to-date scheduling.
- Installable progressive web app with versioned service-worker cache busting so UI changes reach installed devices; an earlier Android wrapper was deliberately retired in favour of the single web codebase.
- Audiobook and "read along" support: long-form narrated books with word-level highlighting, a new-content banner, and a daily health check that exercises the AI-reflection path end to end and self-heals.
- A privacy-minded optional book-search feature (full-text index; the language model only ever sees chapter locations, never book text).
- Regional content support (e.g., localized meeting directories) with clean per-region toggles rather than hard-coded assumptions.
- Maintains a running in-app "What's New" changelog for every user-visible release.

## Stack

Python server, self-hosted TTS/STT (Piper, Kokoro, Whisper/`faster-whisper`), SQLite with encrypted-field support (Fernet), installable PWA, deployed on a cloud server.

## Status

Live, actively developed with regular releases.

## Repositories

- Web/server app — Private: `github.com/reedisthebomb/tenth-step`
