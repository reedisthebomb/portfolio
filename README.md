# Reed's Portfolio

Professional portfolio of software projects, infrastructure work, and Google Career Certificates (via Coursera).

See [SETUP.md](SETUP.md) for how this repo is organized and kept up to date.

## Summary

Full-stack builder and self-hosted-infrastructure operator — production dashboards, real-time data reconciliation across external systems (GIS/mapping data, ticketing platforms, payment processors), self-hosted AI/voice pipelines (TTS/STT, forced alignment), and home/small-business infrastructure (Docker, Tailscale, Home Assistant). Most of the projects below are live systems in real daily use, not tutorials.

## Skills

- **Languages:** TypeScript/JavaScript, Python, Kotlin/Java (Android), SQL, Bash
- **Frontend:** React, Next.js, Vite, Astro
- **Backend:** Node.js, Fastify, Flask, PostgreSQL (Drizzle ORM), SQLite/libSQL, REST API design
- **Infrastructure:** Docker Compose, Tailscale (private mesh networking), self-hosted deployment, backup/restore & rollback procedures
- **Integrations:** Valhalla road routing, n8n workflow automation (HMAC-signed webhooks), Square (payments/Terminal), Jotform, GIS/mapping data (Vetro, GeoCall), Home Assistant, Swiss Ephemeris astronomical data
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

See [`/projects`](projects/README.md) for the full list with descriptions, stacks, and status. Highlights (see the full list for another ten):

- **[Fiber Locator Dashboard](projects/fiber-locator-dashboard.md)** — production cloud dashboard reconciling multi-source GIS/ticketing data, with a smart daily route planner (self-hosted Valhalla) and a native Android companion app on the Play Store.
- **[Network Topology Agent](projects/network-topology-agent.md)** — self-hosted NOC dashboard: live topology mapping, security triage, automated health checks.
- **[Convention Registration Desk](projects/convention-registration.md)** — full-stack event operations platform: payments, badge printing, check-in, financial reconciliation, e2e-tested.
- **[Tenth Step Companion](projects/tenth-step.md)** — web app with a full self-hosted voice pipeline (TTS narration, STT input, forced text/audio alignment).
- **[District 12 Service Command Center](projects/district12-command-center.md)** — private nonprofit treasurer/secretary platform: audited ledger with split payments, budgets vs. actual, strict separation of duties, nightly off-site backups.
- **[Tech It Easy](projects/tech-it-easy.md)** — business website and operations platform in one Next.js app: request funnel, leads → tickets → estimates → projects, n8n automation, optional local AI, animated SVG illustrations, e2e- and accessibility-tested.
- **[Coatings & More](projects/coatings-and-more.md)** — estimate/invoice PWA for a painting contractor: exact integer-cent pricing (forward and backward), mutually exclusive alternative options, immutable per-revision PDFs, and an idempotent historical import.

## How this portfolio is organized

```
portfolio/
├── README.md              ← this file
├── SETUP.md                ← how to maintain, extend, and publish this repo
├── projects/                ← one write-up per project, plus an index
└── certifications/           ← one folder per Google/Coursera certificate, plus an index and a template
```

## Contact

- **Email:** reedisthebomb.com@gmail.com
- **LinkedIn:** [linkedin.com/in/jimmie-clark-507414194](https://www.linkedin.com/in/jimmie-clark-507414194)
