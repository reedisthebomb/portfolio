# Projects

All projects below are real, working systems — most are in active production use, not tutorials or toy apps. Repos marked **Private repository** are hosted on GitHub under private visibility; "available on request" means the code lives locally and hasn't been pushed to GitHub yet (see the main [SETUP.md](../SETUP.md) for the plan to get each one audited and published).

| Project | What it is | Stack | Status |
|---|---|---|---|
| [Fiber Locator Dashboard](fiber-locator-dashboard.md) | Cloud dashboard for fiber-locate ticket operations, multi-source GIS data reconciliation | Node.js, React, Android | Live |
| [Network Topology Agent](network-topology-agent.md) | Self-hosted NOC dashboard: live topology, security triage, health monitoring | Docker Compose, Tailscale | Live — repo stays private permanently (contains live network data), see SETUP.md §5 |
| [Recovery Sponsor Hub](recovery-ahent-12step.md) | AI-backed AA/NA support tool: chat, meeting topics, sharing points grounded in program literature | Node.js, Express | Live |
| [Convention Registration Desk](convention-registration.md) | Full-stack event ops: payments, badges, check-in, reconciliation | TypeScript, React, SQLite, Square, Playwright | Live (event-built) |
| [Cosmic Natal Studio](cosmic-natal-studio.md) | Local-first astrology app with real Swiss Ephemeris calculations | Python, Flask, SQLite | Live |
| [Absolute Beauty](absolute-beauty.md) | Salon business operations dashboard | React 19, TypeScript | Live |
| [Claude Relay](claude-relay.md) | Isolated LLM-access relay avoiding per-token API key exposure | Docker, Tailscale | Live |
| [Home Assistant Agent](home-assistant-agent.md) | CLI automation agent for a real home-automation deployment | CLI, Home Assistant REST API | Active |
| [A.A. District 12 Website](district-12-website.md) | Public information site for a regional service district | Astro | Draft |
| [Tenth Step Companion](tenth-step.md) | Personal-development app with a self-hosted TTS/STT/forced-alignment voice pipeline | Python, Piper/Kokoro TTS, Whisper, Android | Live |
| [Step Companion](recovery-step-companion.md) | Native Android app with sponsor-review state machine | Android/Kotlin | Prototype |
| [Our Life on the Daily](our-lives-platform.md) | Household coordination platform: shared scheduling, voice-note capture | TypeScript, Vite, React | Early prototype |
| [Spiritual Principle of the Day](spiritual-principle-day.md) | Rotating content panel embedded in Home Assistant | Static HTML/JS | Live |
| [Windows Music Agent](windows-music-agent.md) | Scoped, password-free remote access setup for a production workstation | SSH, bash | In use |

**In planning:** a camera-integration platform (`yi-camera-platform`) is scoped but not yet built — left off the table above until there's working code to show.

**Deliberately excluded:** a cloned third-party open-source repository (not original work) and internal device-migration/staging folders (not standalone projects) are not listed here, in line with keeping this portfolio to work that is actually mine.
