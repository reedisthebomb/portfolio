# Claude Relay

**One line:** Isolated relay container that gives internal apps LLM access through a subscription login instead of a metered, billable API key.

## Overview

A small but deliberate infrastructure project solving a real cost/security problem: apps that call the Anthropic API directly need an API key billed per token, and a leaked or misused key can drain a balance with no recourse. Claude Relay isolates that risk by authenticating through a Claude subscription login instead, and by refusing to expose itself outside a private mesh network.

## Engineering highlights

- No `ANTHROPIC_API_KEY` ever held by calling applications — eliminates an entire class of key-leak/billing-drain risk.
- Runs in an isolated, locked-down container.
- Reachable only over Tailscale — never bound to a public port.
- Designed for realistic low-volume personal-tool usage rather than high-traffic product load, so the cost/complexity tradeoff is deliberately matched to the actual use case.

## Stack

Containerized service, Tailscale-gated networking, Claude Code subscription auth.

## Status

Live, backing other internal projects' AI features.

## Repository

Private — [github.com/reedisthebomb/claude-relay](https://github.com/reedisthebomb/claude-relay)
