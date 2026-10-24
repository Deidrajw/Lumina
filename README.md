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


## Latest development candidate
[Phase D v0.9.5-beta.4](docs/PHASE_D_IMPORT_DISPLAY_SAFETY_2026-10-24.md): unified Vault/Settings backup restore, display safety, import save feedback; draft review branch only, no main deployment. Prior Beta 3 preview was confirmed to open in iPhone Safari by the user; photo backup and Safari workflow tests still required.


## October 24 UI/UX review and beta.5
[Complete UI/UX heuristic audit](docs/AUDIT_UIUX_FULL_2026-10-24.md) compares all app areas against the user's study guide, with measured findings, priority and acceptance criteria. [Interactive six-screen proposal](docs/prototypes/UIUX_Concept_Studio.html) uses fictional data and does not save records; proposed reorganizations need approval. The actual v0.9.5-beta.5 code contains small accessibility foundation changes only, stacked on beta.4. Production main remains v0.9.4.
