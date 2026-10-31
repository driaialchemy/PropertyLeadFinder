# AGENTS.md

## Purpose

Cloudflare Worker demo that ranks synthetic Arizona property leads. It has no auth and no database.

## Setup

npm install
npm run dev

## Tests

No automated suite. After behavior changes, check `/` and `/api/leads`.

## Sensitive areas

`wrangler.toml` (deploy config; do not edit), `.env` files, `data.json`, and `sample_data/`.

## Approval gates

Human approval is required before dependency changes, external-call changes, deploy or container config, secrets, and AI-provider or database config.

## Verification

No test suite is present. Re-read every changed file. Run tests after every change once a suite exists.
