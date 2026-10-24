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
