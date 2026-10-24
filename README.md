# Lumina
Premium mobile-first personal wellness tracker. Current app: root `index.html` (HTML/CSS/JS), v0.9.4 on GitHub `main`. Cloudflare Pages deployment is planned, not yet verified.

Start each development session with `PROJECT_INSTRUCTIONS.md`, `docs/PROJECT_STATE.md`, and `docs/CONTINUITY_LOG.md`. Read requirement, bug, QA and architecture docs before changing code.

## Project documentation
- PROJECT_INSTRUCTIONS.md — rules governing work
- docs/PROJECT_STATE.md — what actually exists and what is next
- docs/CONTINUITY_LOG.md — session-to-session handoff
- docs/REQUIREMENTS_REGISTER.md — requirements and approval status
- docs/KNOWN_BUGS.md — reproduction and severity
- docs/CHANGELOG.md — release-by-release history
- docs/QA_REGRESSION.md — repeatable test matrix
- docs/ARCHITECTURE.md — storage/data contracts
- docs/DESIGN_SYSTEM.md — visual decisions
- docs/ROADMAP.md and docs/DECISIONS.md — priorities and rationales
- docs/DEPLOYMENT_CLOUDFLARE.md and docs/RELEASE_CHECKLIST.md — shipping process

Public repo: never store actual personal wellness data, photos, backups or secrets here.
## Latest audit
[2026-10-24 v0.9.4 functional/UI/UX audit](docs/AUDIT_2026-10-24.md) — isolated browser tests, code-confirmed data risks, release gates and roadmap. No changes made to production app.


## Latest implementation candidate
[Phase B v0.9.5-beta.2 stability notes](docs/PHASE_B_STABILITY_2026-10-24.md). This beta is stacked on Phase A and governance PRs, and does not modify production main.


## Latest candidate
[Beta.3 release hardening](docs/PHASE_C_HARDENING_2026-10-24.md) — stacked review branch, not production. Real Safari/IDB/security checks required before any main merge.
