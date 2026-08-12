# Windows Music Agent

**One line:** Secure, controlled remote-access setup letting an automation agent inspect and manage a music-production workstation without ever holding user passwords.

## Overview

An infrastructure/access-configuration project: rather than granting broad or credential-based access to a Windows music-production machine (Studio One Artist, Guitar Rig, Fender FUSE, plugin/preset management), this defines a scoped SSH-based access path plus explicit operating rules for what an automation agent is and isn't allowed to touch.

## Engineering highlights

- Password-free access model — SSH key-based, scoped, and testable independently (`scripts/test-windows-access.sh`).
- Written operating rules (`AGENTS.md`) constraining what automated changes are permitted, treating agent access as a security boundary, not a convenience shortcut.
- Cross-platform integration point between a Linux automation host and a Windows production workstation.

## Stack

SSH, bash tooling, cross-platform (Linux ↔ Windows) automation.

## Status

Setup/infrastructure, in use.

## Repository

Private — available on request (not yet published to GitHub).
