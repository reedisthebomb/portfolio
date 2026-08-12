# Spiritual Principle of the Day

**One line:** Small static content service integrated as a live panel inside a Home Assistant dashboard.

## Overview

A lightweight static page that rotates featured content daily using a deterministic yearly shuffle (so content doesn't repeat in the same order every year), deployed both as a standalone page and embedded directly into a Home Assistant sidebar via `panel_iframe`.

## Engineering highlights

- Deterministic yearly shuffle algorithm instead of random repeats or a fixed list order.
- Client-side day-rollover handling: the page refreshes its own countdown and swaps content at local midnight without a page reload.
- Deployed to a home server (Kali-hosted) and wired into Home Assistant's own configuration (`configuration.yaml`) as a native-feeling panel, plus exposed over HTTPS via a public DuckDNS vhost.

## Stack

Static HTML/JS, nginx-served, Home Assistant `panel_iframe` integration.

## Status

Live.

## Repository

Private — [github.com/reedisthebomb/spiritual-principle-day](https://github.com/reedisthebomb/spiritual-principle-day)
