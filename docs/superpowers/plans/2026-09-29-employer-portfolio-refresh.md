# Employer Portfolio Refresh Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Publish a current, employer-readable GitHub portfolio at the existing résumé URL without exposing private project source or operational data.

**Architecture:** The public Markdown repository remains the portfolio surface. The landing README provides the recruiter-facing summary, the project index provides discoverability, and one Markdown case study per project provides evidence-based detail. GitHub repository metadata improves the profile preview; no separate hosted site is introduced.

**Tech Stack:** GitHub repository metadata, Markdown, GitHub-rendered README.

**Spec:** `docs/superpowers/specs/2026-09-29-employer-portfolio-refresh-design.md`

## Global Constraints

- Preserve `https://github.com/reedisthebomb/portfolio` as the résumé destination.
- Do not make any private repository public or link visitors to private source.
- Keep Network Topology Agent private permanently; do not disclose network identifiers, credentials, personal records, or financial data.
- Use only claims supported by the current repository documentation and commit history.
- Do not enable GitHub Pages.

## Review Focus

- Every GitHub link exposed in public content must return a public HTTP 200 response.
- Project prose must not contain tailscale URLs, ports, internal host names, credential names, or real operational data.
- The new District 12 Command Center case study must describe a private service tool at a high level only.
- Relative Markdown links must resolve from GitHub’s rendered README and projects index.
- The résumé URL must still return HTTP 200 without authenticated GitHub access after push.

---

### Task 1: Refresh the landing page and project index

**Files:**
- Modify: `README.md`
- Modify: `projects/README.md`

**Interfaces:**
- Consumes: verified latest commits and project documentation from the local project repositories.
- Produces: a recruiter-readable landing page and complete project list that link only to public portfolio content.

- [ ] **Step 1: Write the content-validation checklist**

Create a temporary checklist for required current highlights (District 12 Command Center, Fiber Locator Dashboard, Convention Registration Desk, Home Assistant Agent, Claude Relay, and Network Topology Agent), prohibited internal details, and public-link requirements.

- [ ] **Step 2: Run the checklist against the current README and index**

Run: `rg -n 'District 12 Command Center|tail.*net|github.com/reedisthebomb/(fiber\.locator\.dashboard|network-topology-agent)' README.md projects/README.md`

Expected: the command demonstrates the missing new project and identifies any inaccessible links that must not remain.

- [ ] **Step 3: Update the landing summary and current highlights**

Modify `README.md` to lead with practical software and infrastructure outcomes, add District 12 Command Center to the highlights, and use link labels that point only into this public portfolio.

- [ ] **Step 4: Update the project table**

Modify `projects/README.md` to add District 12 Command Center and refresh the verified-status wording for the six current systems, without changing private repository visibility or exposing URLs to their source.

- [ ] **Step 5: Run local Markdown-link and privacy checks**

Run: `rg -n '\]\([^)]*\.md\)' README.md projects/README.md` and `rg -n -i 'tail.*net|192\.168\.|localhost|password|session_secret|api[_-]?key' README.md projects/README.md`

Expected: every referenced Markdown target exists; the privacy scan has no matches.

- [ ] **Step 6: Commit the landing-page refresh**

```bash
git add README.md projects/README.md
git commit -m "docs: refresh employer portfolio overview"
```

### Task 2: Add the District 12 Command Center case study and safely revise current cases

**Files:**
- Create: `projects/district12-command-center.md`
- Modify: `projects/fiber-locator-dashboard.md`
- Modify: `projects/convention-registration.md`
- Modify: `projects/home-assistant-agent.md`
- Modify: `projects/claude-relay.md`
- Modify: `projects/network-topology-agent.md`

**Interfaces:**
- Consumes: Task 1’s index link and current project docs/commit history.
- Produces: accessible Markdown case studies with accurate, non-sensitive descriptions.

- [ ] **Step 1: Write the case-study content checks**

Specify a Markdown-only test: the new file must have one-line summary, overview, engineering highlights, stack, status, and a private/source-availability statement; all refreshed files must retain the same sections and no inaccessible GitHub URLs.

- [ ] **Step 2: Run the case-study checks before editing**

Run: `test -f projects/district12-command-center.md; printf '%s\n' $?` and `rg -n 'github.com/reedisthebomb/' projects/*.md`

Expected: the first command reports `1`; the second identifies private-source references to remove or convert to non-link availability statements.

- [ ] **Step 3: Create `projects/district12-command-center.md`**

Describe the private District 12 service-operations application as a Next.js, TypeScript, PostgreSQL/Drizzle system supporting distinct finance and secretary workflows, governance-aware records, imports, testing, and controlled AI assistance. Do not mention the organization’s internal URL, user names, unpublished data, or finance controls.

- [ ] **Step 4: Revise the five current case studies from verified evidence**

Add only recent, supportable outcomes: stale-device comment preservation in Fiber Locator; attendee/badge synchronization in Convention Registration; CLI health-check improvements in Home Assistant Agent; relay watchdog reliability in Claude Relay; and removed-container health-state correction in Network Topology Agent. Keep Network Topology’s permanent private status.

- [ ] **Step 5: Run structure and privacy validation**

Run: `for f in projects/district12-command-center.md projects/{fiber-locator-dashboard,convention-registration,home-assistant-agent,claude-relay,network-topology-agent}.md; do rg -q '^## Overview$' "$f" && rg -q '^## Engineering highlights$' "$f" && rg -q '^## Stack$' "$f" && rg -q '^## Status$' "$f" || exit 1; done` and `rg -n -i 'tail.*net|192\.168\.|localhost|password|session_secret|api[_-]?key' projects/*.md`

Expected: the structure command exits 0; the privacy scan has no matches.

- [ ] **Step 6: Commit the case studies**

```bash
git add projects/
git commit -m "docs: add current project case studies"
```

### Task 3: Publish and verify public access

**Files:**
- Modify remotely: GitHub repository metadata for `reedisthebomb/portfolio`

**Interfaces:**
- Consumes: Tasks 1 and 2’s committed portfolio content.
- Produces: a pushed public repository and independently checked résumé destination.

- [ ] **Step 1: Set the public repository description**

Use GitHub CLI to set a concise description: `Professional portfolio: production software, infrastructure, and systems case studies.` Do not set a homepage.

- [ ] **Step 2: Push `main`**

Run: `git push origin main`

Expected: push succeeds and the remote commit matches local `HEAD`.

- [ ] **Step 3: Verify the public repository metadata and public URL**

Run: `gh api repos/reedisthebomb/portfolio --jq '{visibility,description,html_url,pushed_at}'` and `curl -sS -o /dev/null -w '%{http_code}\n' https://github.com/reedisthebomb/portfolio`

Expected: visibility is `public`, the description matches Step 1, and the URL returns `200`.

- [ ] **Step 4: Inspect public links without authenticated GitHub access**

Run: `curl -sS https://raw.githubusercontent.com/reedisthebomb/portfolio/main/README.md | rg 'github.com/reedisthebomb/'`

Expected: no direct links to private project repositories appear.

- [ ] **Step 5: Record final evidence in the handoff**

Update `README.md` only if a concise public-maintenance note is needed; otherwise report the verified URL, commit SHA, and check results in the task handoff without storing secrets.

## Self-review

- Spec coverage: Task 1 preserves the résumé route and discoverability; Task 2 implements accurate private-safe case studies; Task 3 updates metadata, publishes, and independently checks access.
- Step scan: each task has an explicit pre-edit check, a specific content or publication operation, validation, and commit/push checkpoint.
- Type consistency: this Markdown-only plan has no programmatic interfaces; all project-file names match the repository index.
- Review focus: privacy scans and unauthenticated public URL/link checks are assigned to Tasks 1–3.
- Proportion: three tasks cover a seven-file documentation refresh plus one metadata change without adding an unnecessary web application.
