# Requirements
Statuses: Requested | In Progress | Implemented | Verified | Blocked | Superseded. Only evidence-backed results become Verified. Record approved/LOCKED behavior.

| ID | Requirement | Priority | Status | Acceptance |
|---|---|---|---|---|
| LUM-001 | Versioned project docs + continuity | P0 | In Progress | GitHub docs, changelog, QA and handoffs are maintained |
| LUM-002 | Cloudflare Pages Git integration and environments | P1 | Requested | main production, PR preview, release/rollback validated |
| LUM-003 | Comprehensive UI/UX audit | P1 | Requested | All screens analyzed with prioritized evidence before implementation |
| LUM-004 | End-to-end functional audit | P0 | Requested | Reproducible defects, tests, QA evidence |
| LUM-005 | Full data portability with photos | P0 | Requested | Export + new-origin import restores records, linked images |
| LUM-006 | Isolated test/sample environment | P1 | Requested | No writes or merges into real records |
| LUM-007 | Responsive and reliable workflows | P1 | Requested | Safe areas, modal exits, search, reorder and photo save work |

Template: ID / title / requested date / screens / functions / data impact / dependencies / expected / acceptance / priority / status / evidence / PR.
## 2026-10-24 Audit outcomes and proposed work
LUM-003/LUM-004: Audit report produced (CODE REVIEW + PARTIAL AUTOMATED TESTS); remain **In Progress** pending real Safari/Cloudflare/IndexedDB E2E. Do not label Verified. LUM-002: user reports Cloudflare URL deployed, connector verification pending.

| Requirement ID | Priority | Status | Acceptance |
|---|---|---|---|
| LUM-008 | P0 | Requested | Photo add/remove during edit must be committed only on successful parent save; Cancel/failed save preserves previous blobs and refs |
| LUM-009 | P0 | Requested | Full photo backup restore to separate clean origin; protect existing user data and IDs |
| LUM-010 | P0 | Requested | Full reset deletes intended localStorage AND IndexedDB data, with explicit confirmation and test evidence |
| LUM-011 | P1 | Requested | Progress photo persists reliably; quota errors preserve draft; all image entities use consistent storage |
| LUM-012 | P1 | Requested | Vault cleanup works with populated records and no undefined variables |
| LUM-013 | P1 | Requested | Render imported or typed text without HTML/script execution |
| LUM-014 | P1 | Requested | Calendar days, streaks, exports correct at evening/DST/timezone boundaries |
| LUM-015 | P1 | Requested | Demo preview enforces data isolation across every writer/delete/import and migrations |
| LUM-016 | P2 | Requested | Modal keyboard/back/outside tap reliable with unsaved form protection |
| LUM-017 | P2 | Requested | Fix Smart Capture wording, version banner, density, contrast and touch-size issues |

See `AUDIT_2026-10-24.md` for test statuses and UI review.

## 2026-10-24 Phase A update
- LUM-008 staged photo edit/cancel/save semantics — **IMPLEMENTED beta**, NOT VERIFIED Safari/IDB.
- LUM-009 photo-complete backup/import with confirmation and rollback attempt — **IMPLEMENTED beta**, NOT VERIFIED clean origin.
- LUM-010 full localStorage+IDB clear — **IMPLEMENTED beta**, NOT VERIFIED iPhone.
- LUM-011 progress IDB photo + failure-safe form — **IMPLEMENTED beta**, NOT VERIFIED quota/real restore.
Acceptance tests still pending; see `PHASE_A_DATA_INTEGRITY_2026-10-24.md`. Other audit issues remain Requested.


## 2026-10-24 Phase B implementation status
LUM-012 / LUM-BUG-013 Vault Cleanup: IMPLEMENTED beta. Populated automated isolated PASS, real Safari NOT TESTED.
LUM-013 / LUM-BUG-014 Safe text rendering: PARTIALLY IMPLEMENTED beta in key Today/Body/Vault/Insights/Timeline renderers, synthetic injection PASS; full inline-HTML security review remains OPEN.
LUM-014 / LUM-BUG-015 Local dates: IMPLEMENTED beta; Toronto evening date test PASS, legacy DST and doctor exports NOT TESTED.
LUM-015 / LUM-BUG-019 Demo isolation: IMPLEMENTED beta for central save/load and photo primitives, simulated PASS. All direct localStorage/migration paths NOT FULLY AUDITED.
Do not mark Verified before actual browser, Safari, empty/populated and failure testing. See PHASE_B_STABILITY_2026-10-24.md.


## 2026-10-24 Phase C beta.3
LUM-016 / BUG-017 Escape foremost overlay implemented candidate (isolated PASS); complete focus/outside-tap/unsaved-state coverage NOT TESTED. LUM-017 / BUG-016 Smart Capture now honestly requests manual entry (isolated PASS). LUM-013 output safety expanded to printable Doctor Export and Recent Capture entries (malicious fixture PASS), full app injection audit OPEN. LUM-015 sample-preview flag persistence blocked in tested paths (PASS), full direct write review OPEN. Real iPhone/Cloudflare photo round-trip required before any feature Verified.


### 2026-10-24 Phase D candidate requirements
- **LUM-018 | P0 | Implemented beta** — Vault .json import must use Settings's validated photo-inclusive confirmed REPLACE flow and rollback attempt; test with fake file/real FileReader passed; actual IDB import NOT TESTED.
- **LUM-019 | P1 | Partially Implemented beta** — Escape user-supplied text in product detail, linked conditions/journal, CSV mapping/preview, global-search renderer, Rx custom chips; malicious synthetic event fixture did not execute; comprehensive full-app sink audit OPEN.
- **LUM-020 | P1 | Implemented beta** — CSV import guards Sample Preview and returns failure without false success; Home Screen build info reflects version, activity seeding flag writes only after success; simulated PASS.
**Acceptance before Verified:** actual Cloudflare preview and iPhone Safari, valid photo-backed restore across origins, navigation and import failure recovery, all display/input paths/security regression.


### 2026-10-24 — UI/UX audit requirements
**LUM-021 | P1 | IMPLEMENTED beta.5 (not Verified)** — Accessible visual foundation. Affected all screens CSS/nav plus switchTab: contrast >=4.5 on main text surfaces, nav label >=11px, Settings icon 44px, tab targets, 16px Safari text fields, browser zoom, focus outlines, reduced motion, aria-current. Regression: render 5 widths × both themes, keyboard/VoiceOver/large text, no clipped overlays; no data migration.
**LUM-022 | P1 | PROPOSED** — Today focus and alerts hierarchy: primary log/true bounded progress, needs-attention summary and expanded details. Risk: hiding urgent reminders or changing ring meaning; acceptance 5-second task discovery, all alerts reachable, denominators defined; *do not implement until preview approval*.
**LUM-023 | P1 | PROPOSED** — Vault searchable grouped inventory, summary needs review, product form disclosure; preserve existing create/edit/link IDs, filter/search return; test 20+ products. *Approval required*.
**LUM-024 | P1 | PROPOSED** — Insights observation + timeframe/sample size/evidence, group secondary analysis; no unsupported causation or effectiveness claim. *Approval required*.
**LUM-025 | P1 | PROPOSED** — Body/Protocols clear task-first actions, appropriate tabs and advanced filters, non-drag reorder alternative; complete CRUD and accessible states. *Approval required*.
**LUM-026 | P1 | REQUESTED** — consistent save/error/empty/draft recovery across all forms, confirm data persistence including photos; all mobile failure scenarios.
**LUM-027 | P2 | REQUESTED** — actual Safari VoiceOver, enlarged text, zoom, keyboard focus, LCP/INP/CLS and accessibility baseline; distinguish measured from assumed performance.
Older LUM-008–020 beta fixes remain not verified for full cross-origin IDB/photo/whole-app QA. Full details and risks: docs/AUDIT_UIUX_FULL_2026-10-24.md.
