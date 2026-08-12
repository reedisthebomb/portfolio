# Setup & Maintenance Guide

This document explains how this portfolio repo is put together, how to keep it current, and how to safely take it public when you're ready. Keep this file — it's the instruction manual for the whole thing.

---

## 1. Repo layout

```
portfolio/
├── README.md                  Main landing page: summary, skills, project & cert highlights
├── SETUP.md                   This file
├── projects/
│   ├── README.md               Index table of every project
│   └── <project-name>.md       One write-up per project
└── certifications/
    ├── README.md               Index table of every certificate
    ├── _template/README.md      Copy this to start a new certificate
    └── <certificate-slug>/README.md   One folder per certificate
```

Nothing in here duplicates your actual project code — this repo is an **index and showcase**, not a copy of every repo's source. Each project write-up links out to that project's real GitHub repo (or says "available on request" if it isn't published yet).

---

## 2. Adding a new project

1. Create `projects/<project-name>.md` using the existing files as a template: one-line tagline, Overview, Engineering highlights (bullet list of what's actually technically interesting), Stack, Status, Repository link.
2. Add a row to the table in `projects/README.md`.
3. Add a highlight bullet to the main `README.md` **only** if it's one of your best 4-5 projects — keep the front page tight.
4. If the underlying repo isn't on GitHub yet, see §5 before linking to it.

## 3. Adding a new certificate (do this every time you finish or start one)

1. Copy the template folder:
   ```bash
   cp -r certifications/_template certifications/<certificate-slug>
   ```
   e.g. `certifications/google-data-analytics`
2. Fill in the front-matter: status, start date, completion date, **Credential ID**, and **Verify link**.
   - Coursera and Credly both email you a claim link when you finish a certificate. Claim it, then copy the public verification URL from Credly (and/or the Coursera certificate share link) into this field.
   - Since 2025, LinkedIn auto-verifies Coursera/Credly certificates once you connect them — worth doing on your LinkedIn profile too, separately from this repo.
3. Check off coursework as you complete each course.
4. Drop the downloaded certificate PDF / Credly badge PNG into that same folder.
5. Add a row to `certifications/README.md`, and update the status table near the top of the main `README.md`.
6. If the certificate had a capstone/portfolio project worth showing, give it its own file under `projects/` too and cross-link both directions.

## 4. Committing changes

Standard git flow — this repo has no build step, it's pure markdown:

```bash
cd ~/portfolio
git add -A
git commit -m "Add Google Data Analytics certificate progress"
git push
```

---

## 5. Projects not yet published to GitHub

As of 2026-08-12, everything except **`network-topology-agent`** has been audited and pushed as new **private** GitHub repos: `absolute-beauty`, `convention-registration`, `district-12-website`, `home-assistant-agent`, `our-lives-platform`, `recovery-step-companion`, `spiritual-principle-day`, `windows-music-agent`. Each was checked first — `.gitignore` reviewed/hardened, filenames and git history grepped for secret patterns, and (for repos that already had git history) the full commit history scanned for ever-committed `.env`/key/credential files — before the first push. Nothing sensitive was found; `our-lives-platform`'s real `.env.local` was confirmed gitignored (only the safe `.env.example` template got committed).

**`network-topology-agent` is intentionally held back.** Its `data/` folder is already tracked in git and contains live network inventory — `devices.json`, raw `nmap` scan output, discovery logs — real IPs, hostnames, and device fingerprints for the actual home network this dashboard monitors. That's meaningfully more sensitive than "a stray API key" because it's reconnaissance data about a real, currently-running network, and it's already baked into the repo's commit history, not just sitting in the working tree. Two ways forward:
1. **Scrub it first**: add `data/` (or the specific inventory files) to `.gitignore` going forward, then rewrite history to strip it retroactively (`git filter-repo` is the modern tool for this — do this *before* the first push, since rewriting published history is far messier) — then push clean.
2. **Push as-is, keep it private indefinitely**: acceptable if this repo specifically is never meant to go public, even after the rest of the portfolio does.

This needs an explicit decision rather than a default — say the word on which way to go and it'll get done.

**Safe process for any future repo**, one at a time:

1. Confirm/write a `.gitignore` that excludes `.env*`, `node_modules/`, build output, `*.sqlite*`, `backups/`, and any credential/key files.
2. Grep for likely secrets before the first commit:
   ```bash
   grep -RniE "api[_-]?key|secret|password|token|BEGIN (RSA|PRIVATE) KEY" . \
     --exclude-dir={node_modules,.git,build,dist}
   ```
3. If the repo already has git history, also check what's *ever* been committed, not just the current working tree:
   ```bash
   git log --all --diff-filter=A --name-only --pretty=format: | sort -u | grep -iE '\.env|secret|credential|\.pem$|\.key$|token'
   ```
4. `git init` (if not already), stage, and review `git status` — actually look at the file list before the first commit, not just trust the `.gitignore`.
5. Create the GitHub repo **private** first: `gh repo create reedisthebomb/<name> --private --source=. --push`
6. Update that project's write-up in `portfolio/projects/` with the real repo link.

---

## 6. Going public

The portfolio repo itself was created **private**. When you're ready for employers to see it:

```bash
gh repo edit reedisthebomb/portfolio --visibility public
```

Before flipping it:
- [ ] Fill in the **Contact** section at the bottom of `README.md`.
- [ ] Decide, project by project, whether each linked repo should also go public, stay private with "available on request," or be dropped from the portfolio entirely. Flipping the portfolio public does **not** auto-flip the linked repos — that's a separate, deliberate decision per repo.
- [ ] Re-read every project write-up once more for anything you wouldn't want an employer to see (this repo currently includes personal/recovery-themed projects on your explicit instruction — that's a legitimate choice, just make it consciously each time you touch visibility).
- [ ] Optional: enable **GitHub Pages** (Settings → Pages → deploy from `main`) once public, so the README renders as an actual site instead of just a GitHub repo page.

## 7. Sharing selectively before going fully public

You don't have to choose between "fully private" and "fully public." While the repo is private, you can grant a specific person read access without publishing anything:

```bash
gh repo add-collaborator reedisthebomb/portfolio <their-github-username> --permission read
```

They'll get an email invite and can view (not edit) the repo once accepted. Remove access the same way with `gh api -X DELETE repos/reedisthebomb/portfolio/collaborators/<username>`.

---

## 8. What's deliberately left out, and why

- **`headroom`** — this is a clone of someone else's open-source project (`chopratejas/headroom`), not original work. Left out entirely per your "no copyrighted material" instruction.
- **`device-imports`** — a raw device-state/staging folder (contains `auth.json` and session/log databases), not a demo-able project, and not safe to publish as-is.
- **`migration-intake`** — a working folder for consolidating files across devices before they become real projects, not a project itself.
- **`convention-status-viewer`** — a one-page companion status site for Convention Registration; mentioned there rather than getting its own full write-up since it's a thin artifact, not a separate system.
- **`yi-camera-platform`** — currently just planning notes (`AGENTS.md`), no working code yet. Noted as "in planning" in `projects/README.md`; give it a real write-up once there's something to show.
