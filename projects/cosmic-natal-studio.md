# Cosmic Natal Studio

**One line:** Local-first astrology studio with real Swiss Ephemeris astronomical calculations and a hand-built chart-interpretation engine.

## Overview

A privacy-first application that computes natal astrology charts from genuine astronomical data — not simplified formula approximations. Runs entirely on a home server, reachable only over the local network and Tailscale, with no accounts, no analytics, and no third-party calls involving anyone's birth date or location.

## Engineering highlights

- Astronomical accuracy via [pyswisseph](https://github.com/astrorigin/pyswisseph) (Swiss Ephemeris Python bindings) with bundled real ephemeris data files, rather than approximated math.
- Hand-built interpretation engine translating raw chart data into readable output.
- Interactive natal chart wheel UI.
- Saved-people library backed by `sqlite3` for repeat lookups.
- Deliberate privacy architecture: local-first, no external network calls for sensitive personal data (birth date/location).

## Stack

Python, Flask + waitress, stdlib `sqlite3`, pyswisseph.

## Status

Live, self-hosted.

## Repository

Private — [github.com/reedisthebomb/cosmic-natal-studio](https://github.com/reedisthebomb/cosmic-natal-studio)
