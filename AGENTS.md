# AGENTS.md — Homesafe Strata franchise application form

Inherit the universal instructions from `${AGENT_WORKBENCH:-$HOME/agent-workbench}/AGENTS.md`. This file is the project-specific delta.

## Review guidance

Codex PR review should stay high-signal and focus on P0/P1 issues:

- Flag correctness, security, privacy, data loss, authorization, migration, concurrency, billing, deployment, and user-visible workflow regressions.
- Check changed behavior against the closest `AGENTS.md`, existing project patterns, and the affected runtime workflow.
- Treat missing or misleading verification as a review issue when a change touches user-visible behavior, data writes, auth, jobs, billing, or deployment.
- Do not leave low-priority style comments unless they hide a real bug or future maintenance risk.

## Scope and sources of truth

This repository is a static GitHub Pages form for Homesafe Strata franchise applications.

- `index.html` owns the UI, validation, payload mapping, endpoint configuration, and submission behavior.
- `README.md` records the HubSpot endpoint contract and the rule against reusing the building-and-pest form ID.

Do not add a framework, backend, analytics store, or alternate lead-routing system without explicit scope.

## Invariants

- Applicant data is personal and commercially sensitive. Never log, commit, screenshot, or retain real submissions in fixtures.
- Keep the Strata-specific field names aligned with the dedicated HubSpot form. Do not substitute another franchise form ID.
- An unconfigured endpoint must fail clearly without losing user input or claiming success.
- Prevent duplicate submission and preserve accessible validation, focus, error, retry, and narrow-screen behavior.
- A successful request is not end-to-end proof; authorized proof includes the named HubSpot test record and field routing.

## Commands and risk

### Local-safe

```bash
python3 -m http.server 8000
```

Exercise validation with fictitious data and inspect desktop/mobile layouts. Serving locally does not make a real HubSpot submission safe.

### External read-only

Inspecting a deployed page or named HubSpot form/schema is read-only only when no form is submitted and no record is changed.

### External write

Submitting the form creates a HubSpot record. Use only an explicitly approved test identity/account. Endpoint changes, GitHub Pages publication, CRM routing changes, and production deployment require explicit current-turn approval naming the target.

### Destructive or irreversible

Deleting applicant records, bulk editing CRM fields, replacing the live form endpoint, or removing the deployed form requires explicit confirmation and a recovery/rollback plan.

## Verification

Validate required/conditional fields, invalid input, duplicate-click protection, network failure, success state, keyboard flow, and mobile layout. For an authorized integration test, confirm the exact test record and field mapping in HubSpot without exposing applicant data.
