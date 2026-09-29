# Employer Portfolio Refresh Design

## Purpose

Keep the résumé destination, `https://github.com/reedisthebomb/portfolio`, an
employer-readable public portfolio that accurately represents the current
project work without exposing private source repositories or infrastructure
details.

## Audience and success criteria

The primary audience is a hiring manager or recruiter opening the résumé link
without a GitHub account. They must be able to read a concise professional
overview, understand the technical impact of current projects, and reach the
contact information. No visible link may lead them to a private GitHub
repository.

Success means:

- The existing public GitHub repository URL remains unchanged.
- The public README and project index name the current, verified work.
- Private systems are presented as case studies and are labeled clearly rather
  than linked to inaccessible code.
- The repository description makes the profile listing understandable.
- The updated public URL returns HTTP 200 when checked unauthenticated.

## Content approach

The README remains the landing page. It will receive an employer-oriented
opening summary and a concise set of current highlights, including the new
District 12 Command Center. The project index will retain one row per system
and update entries whose recent repository history confirms active work:
District 12 Command Center, Fiber Locator Dashboard, Convention Registration
Desk, Home Assistant Agent, Claude Relay, and Network Topology Agent.

A new project case study will describe District 12 Command Center from its
verified local documentation and latest commits. Existing case studies will
be adjusted only where current evidence supports a change. Claims about live
network data, credentials, participants, payments, or private AI access must
stay high-level and must not reveal operational details.

## Privacy and publication rules

- Do not change visibility of any private repository.
- Do not introduce public links to private repositories.
- Network Topology Agent remains private permanently because its repository
  history contains real network-inventory data.
- Do not copy secrets, personal records, event financial data, or network
  identifiers into the portfolio.
- GitHub Pages is out of scope: the résumé already points to the public GitHub
  repository and that link is the required public destination.

## Verification

Use markdown-link validation for local links, inspect the staged diff for
privacy-sensitive text and inaccessible GitHub URLs, push the public portfolio
commit, then fetch the résumé URL without GitHub authentication and require
HTTP 200.
