# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

`whollyground.io` is a personal domain and content/newsletter platform.

## Infrastructure

- **Domain:** `whollyground.io` — registered via Porkbun
- **Email hosting:** Zoho Mail
- **Transactional email:** SendGrid (used by projects that send automated daily/weekly emails)
- **Publishing platform:** Ghost (under evaluation — chosen for its native email-newsletter-to-subscribers model)
- **M365:** Personal account only — no business/tenant integrations available

## Key Constraints

- SendGrid is the outbound email delivery layer; Zoho handles inboxing.
- Any automation or project that sends email should route through SendGrid.
- Ghost is not yet deployed — architecture decisions around it are still open.
- Do not assume M365 business APIs (Teams, SharePoint, Exchange Online for business) are available.

## Secrets & safety (never do X)

- **Never write a secret into any file that isn't a gitignored `.env`** — not into docs, config, or a permission allowlist. That includes the SendGrid API key, Zoho credentials, and any Ghost/webhook tokens. Cloud-synced folders (Drive/Dropbox) count as exposure, same as git.
- **Never commit a `.env`.** Confirm it's gitignored before any `git add`.
- If a secret is ever pasted into chat or a doc, treat it as burned: rotate it at the provider, then scrub the copy.
