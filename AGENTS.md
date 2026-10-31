version: 1
repository: realestateprospectingapp
risk_level: high
scope:
  summary: Real-estate prospecting web app with deterministic scoring and synthetic hidden-equity data generation.
  preferred_paths:
    - app.js
    - worker.js
    - scoring.js
    - desert.js
    - hero.js
    - faq-widget.js
    - faq-data.js
    - index.html
    - landing.html
    - style.css
    - landing.css
    - README.md
    - generate_synthetic_data_az.py
    - CLAUDE.md
    - AGENTS.md
  restricted_paths:
    - sample_data/synthetic_hidden_equity_data_az.xlsx
    - scoresummary.docx
    - data.json
allowed_actions:
  - edit_static_app_source
  - improve_deterministic_scoring_with_tests_or_docs
  - maintain_synthetic_data_generation
  - update_governance_and_ignore_rules
forbidden_actions:
  - commit_real_prospect_or_homeowner_data
  - commit_private_mls_crm_title_or_financial_exports
  - commit_env_files_or_secret_values
  - add_live_scraping_or_enrichment_without_approval
  - rotate_secrets_without_approval
  - destructive_git_history_rewrite
human_approval_required_for:
  - database_or_supabase_or_postgres_integration
  - crm_email_sms_or_paid_api_integration
  - production_deployment_credentials
  - non_synthetic_personal_or_property_data
  - lead_scoring_rule_changes_affecting_ranking
  - moving_or_deleting_tracked_fixture_exports
  - dependency_changes
  - external_call_changes
  - deploy_or_container_config
  - secrets
  - ai_provider_or_database_config
secrets:
  source: environment_variables_or_platform_managed_secrets
  never_commit:
    - .env
    - .env.*
    - api_keys
    - cloudflare_tokens
    - database_urls
    - supabase_or_postgres_credentials
data_policy:
  allowed: synthetic_or_public_safe_fixtures
  generated_exports_gitignored:
    - "*.xlsx"
    - "*.xls"
    - "*.csv"
    - "*.docx"
  tracked_fixture_notes:
    - "sample_data/synthetic_hidden_equity_data_az.xlsx is a synthetic sample export; do not replace with real data."
    - "scoresummary.docx is a local summary fixture; do not replace with private data."

# Audit remediation metadata
audit_path: audit/multi_repo/2026-09-18/repo_realestateprospectingapp_20260918T004905Z.json
risk_level: HIGH
human_review_required: true
audit_findings:
  - "Spreadsheet/data export files found: synthetic_hidden_equity_data_az (1).xlsx"
  - "Cloud deployment configuration present: wrangler.toml"
  - "Risk level is HIGH, expected LOW."
  - "Missing CLAUDE.md."
  - "Dependency manifests present: package.json"
  - "Missing CLAUDE.md ? no agent policy defined."
  - "Missing AGENTS.md ? no machine-readable safety policy."

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
