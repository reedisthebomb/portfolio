# Reed's Portfolio

Professional portfolio of software projects, infrastructure work, and Google Career Certificates (via Coursera).

> **Status:** private while in progress. See [SETUP.md](SETUP.md) for how this repo is organized, how it's kept up to date, and the plan for making it public.

## Summary

Full-stack builder and self-hosted-infrastructure operator — production dashboards, real-time data reconciliation across external systems (GIS/mapping data, ticketing platforms, payment processors), self-hosted AI/voice pipelines (TTS/STT, forced alignment), and home/small-business infrastructure (Docker, Tailscale, Home Assistant). Most of the projects below are live systems in real daily use, not tutorials.

## Skills

- **Languages:** TypeScript/JavaScript, Python, Kotlin/Java (Android), SQL, Bash
- **Frontend:** React, Vite, Astro
- **Backend:** Node.js, Flask, SQLite/libSQL, REST API design
- **Infrastructure:** Docker Compose, Tailscale (private mesh networking), self-hosted deployment, backup/restore & rollback procedures
- **Integrations:** Square (payments/Terminal), Jotform, GIS/mapping data (Vetro, GeoCall), Home Assistant, Swiss Ephemeris astronomical data
- **AI/voice engineering:** self-hosted TTS (Piper, Kokoro), self-hosted STT (Whisper/`faster-whisper`), forced audio/text alignment, LLM-relay infrastructure
- **Testing:** Vitest, Playwright (e2e)
- **Security-conscious design:** RBAC, audit logging, encrypted-field storage (Fernet), password-free scoped SSH access, network-gated (Tailscale-only) services

## Certifications

See [`/certifications`](certifications/README.md) for Google Career Certificates completed and in progress via Coursera, each with credential ID and public verification link once issued.

| Certificate | Status |
|---|---|
| Google Cybersecurity Professional Certificate | In progress |
| AI Fundamentals | ✅ Completed 2026-07-23 |

## Projects

See [`/projects`](projects/README.md) for the full list with descriptions, stacks, and status. Highlights:

- **[Fiber Locator Dashboard](projects/fiber-locator-dashboard.md)** — production cloud dashboard reconciling multi-source GIS/ticketing data, with a native Android companion app on the Play Store.
- **[Network Topology Agent](projects/network-topology-agent.md)** — self-hosted NOC dashboard: live topology mapping, security triage, automated health checks.
- **[Convention Registration Desk](projects/convention-registration.md)** — full-stack event operations platform: payments, badge printing, check-in, financial reconciliation, e2e-tested.
- **[Tenth Step Companion](projects/tenth-step.md)** — web + Android app with a full self-hosted voice pipeline (TTS narration, STT input, forced text/audio alignment).
- **[Cosmic Natal Studio](projects/cosmic-natal-studio.md)** — local-first app performing real Swiss Ephemeris astronomical calculations.

## How this portfolio is organized

```
portfolio/
├── README.md              ← this file
├── SETUP.md                ← how to maintain, extend, and publish this repo
├── projects/                ← one write-up per project, plus an index
└── certifications/           ← one folder per Google/Coursera certificate, plus an index and a template
```

## Contact

_(add your preferred contact method / LinkedIn / email here when ready to share)_
