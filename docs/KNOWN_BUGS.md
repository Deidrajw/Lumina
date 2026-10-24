# Known Bugs — pending current-build reproduction
| ID | Severity | Evidence / issue | Status |
|---|---|---|---|
| LUM-BUG-001 | Critical | v0.9.4 `exportData()` embeds IndexedDB `_photoBlobs`; `importData()` only restores `KEYS` (code inspected). Photos may be unavailable after restore on another origin. | Open: reproduce |
| LUM-BUG-002 | High | Previous reports: concern/symptom save failed when attaching a photo; photo-storage refactor exists; requires device re-test. | Re-test |
| LUM-BUG-003 | High | Previous reports: supplement search/template picker sometimes blank after typing. | Re-test |
| LUM-BUG-004 | High | Historical: global search > product > edit loses detail screen. | Re-test |
| LUM-BUG-005 | High | Historical: progress photo lightbox lacks reliable exit. | Re-test |
| LUM-BUG-006 | High | Historical: protocol reorder does not work reliably on mobile. | Re-test |
| LUM-BUG-007 | High | Smart Capture must not falsely imply connected label OCR; verify actual behavior. | Audit |
| LUM-BUG-008 | Medium | Header/tab/bottom-nav overlaps and double scrolling on iPhone. | Re-test |
| LUM-BUG-009 | High | `clearAllData()` clears localStorage; IndexedDB photo cleanup not evident in handler. | Audit |

Bug template: ID / date / device / reproduction / expected / actual / severity / root cause / patch PR / regression evidence / status.
## Confirmed new audit findings — 2026-10-24
NOTE: isolated Chromium smoke used mock localStorage; “CODE-CONFIRMED” means source evidence, **not** actual Safari E2E verification.
| ID | Priority | Evidence | Status |
|---|---|---|---|
| LUM-BUG-010 | P0 | removeSympPhoto/removeConcPhoto delete IndexedDB blob before parent save; Cancel can strand old photo reference | CODE-CONFIRMED |
| LUM-BUG-011 | P0 | clearAllData() removes KEYS in localStorage but not IndexedDB blobs | CODE-CONFIRMED |
| LUM-BUG-012 | P0/P1 | saveProgressPhoto() writes base64 to localStorage, ignores failed save and closes | CODE-CONFIRMED |
| LUM-BUG-013 | P1 | Vault Data Cleanup with sample records displays `_invSearchFocused is not defined` | FAIL (isolated automated) |
| LUM-BUG-014 | P1 | malicious fictional concern title executed img.onerror on render | FAIL (isolated automated) |
| LUM-BUG-015 | P1 | today() uses UTC date while day-of-week local; potential evening off-by-one | CODE-CONFIRMED |
| LUM-BUG-016 | P2 | Smart Capture landing promises AI OCR despite manual-only runOCR() | CODE-CONFIRMED |
| LUM-BUG-017 | P2 | Escape does not close regular symptom sheet | FAIL (isolated automated) |
| LUM-BUG-018 | P2 | v0.9.4 app's What's New header says v0.9.3 | CODE-CONFIRMED |
| LUM-BUG-019 | P1 | save() bypasses demo write boundary; direct primitive wrote underlying mock storage; ordinary UI save blocked | AUDIT MUTATORS |
| LUM-BUG-020 | P1 | captured product photo stored inline base64 rather than IDB | CODE-CONFIRMED |
| LUM-BUG-021 | P2 | saveInv logs full product object to console | CODE-CONFIRMED |
| LUM-BUG-022 | P2 | low contrast tertiary text, tiny nav captions, compact tap targets, user zoom restriction | CODE-CONFIRMED |
| LUM-BUG-023 | P2 | overly long dense Today/Insights when populated; safe-area test pending | UX REVIEW |
| LUM-BUG-024 | P2 | monolithic source, duplicate renderer and large inline handler count | CODE REVIEW |

Historical BUG-003 supplement search: PASS isolated with fictional Vault item; BUG-004 detail edit/save: PASS with delayed assertion. BUG-002 photo attach/save, BUG-005 image lightbox and BUG-006 reorder still require real-origin/device test. Full specifics in `docs/AUDIT_2026-10-24.md`.

## 2026-10-24 Phase A candidate status
LUM-BUG-001/010/011/012: code fixes proposed in v0.9.5-beta.1; 17 controlled storage-simulation checks PASS, **not real-device Verified**. Old onboarding Start Fresh partial clear also revised.
Other high-priority findings remain: LUM-BUG-013 Vault Cleanup, 014 unescaped HTML, 015 UTC dates, 019 low-level preview write boundary, and further audit backlog. Do not close issues before regression and Safari/clean-origin verification.


## Phase B 2026-10-24 — evidence and residual risks
LUM-BUG-013: removed undefined search focus variable from renderDataCleanup. Populated fictional record PASS automated isolated. Implemented beta; verification pending.
LUM-BUG-014: prior arbitrary imported HTML executing event handler; targeted escaping in five tab views now blocked tested fixture. Still OPEN as full security audit incomplete (other innerHTML, embedded attributes, product detail).
LUM-BUG-015: UTC date generation replaced with local calendar helpers in frequent paths. Legacy keys untouched; DST/historical/doctor ranges need testing.
LUM-BUG-019: central save denied during preview, load shows fictional data, photo mutation primitives denied; more direct storage side effects require review.
Other historical overlay and cross-view defects still open. Phase A photo migration/backup needs actual Safari and real origin QA.


## 2026-10-24 beta.3
BUG-017 (normal modal Escape) addressed in candidate, isolated Chromium PASS; focus restoration & unsaved prompt not verified. BUG-016 (Smart Capture AI misrepresentation) candidate copy correct, manual entry preserved. BUG-014 additional print/capture HTML sinks candidate escaped; broad app security issue remains OPEN. BUG-019 additional preview persistent flags blocked; all direct localStorage writes not audited. Phase A real photo IDB backup/restore remains BLOCKED. No bugs marked production Verified.


## 2026-10-24 Phase D beta.4
NEW LUM-BUG-025 P0: Vault JSON branch silently replaced stored keys using direct save, bypassing photo-aware validation and confirmation. Candidate fixed by routing to importData; actual FileReader confirmation PASS isolated, real IDB restore NOT TESTED. LUM-018.
LUM-BUG-014 HTML injection risk: additional unsafe HTML paths in product details, journal, linked records, global-search renderer, CSV mapping/preview and custom Rx check-in chip hardened. Synthetic malicious fixture PASS on tested paths. Security remains OPEN until all HTML sinks audited. LUM-019.
NEW LUM-BUG-026 P1: CSV import proceeded or showed success despite write failure/preview; candidate guard and failure feedback. Tested preview write denial; quota/permission real-browser failure NOT TESTED. LUM-020.
NEW LUM-BUG-027 P2: Standalone build label hardcoded beta.2 and demo Developer Reset buttons could write personal flags. Corrected candidate; static inspection, manual Safari pending.
Observation: runSearch renderer has no mounted search-results/search modal in current HTML; test fixture host only. Confirm intended navigation before changing UI, no newly added global search UI this release.


## 2026-10-24 UI/UX audit findings
LUM-BUG-028 P1 (code-confirmed UX): tertiary text tokens low contrast on both themes (dark card ~2.75:1; light white ~2.93:1), bottom navigation 9.5px, Settings control 36px, 14px form inputs and maximum-scale=1. Candidate beta.5 improves contrast/tap/zoom/focus; isolated tests PASS; real Safari/VoiceOver not tested.
LUM-BUG-029 P1 (UX review): populated Today excessive similar alerts/cards and equally weighted four metrics; progress rings have ambiguous zero when none scheduled. Proposed grouped summaries and denominator clarity, not yet implemented.
LUM-BUG-030 P1 (UX review): Vault dense rows with repeated statuses, Insights stacked multiple timeframes, Body/Protocols overflow and alternate reorder path. Proposed designs only.
LUM-BUG-031 P2 (a11y outstanding): 39 static backdrop elements and 268 inline onclick attributes; complete focus, keyboard, accessible names, safe HTML and direct-write audit NOT TESTED. Counts are maintenance scope, not evidence all overlays fail.
Previous data portability, security and preview isolation issues await real Safari/IDB QA. See docs/AUDIT_UIUX_FULL_2026-10-24.md.


## 2026-10-24 beta.6 (approved UX Phase 1)
LUM-BUG-029 Today card overload and unweighted progress total: candidate improved with task-first hierarchy and bounded scheduled count (isolated PASS, real Safari/data NOT VERIFIED).
LUM-BUG-030 Vault/Insights default density: candidate collapsible secondary buckets/evidence; 69 isolated checks PASS; no screen-reader/device verification. Body/Protocols/Settings design debt staged next.
Existing P0 photo clean-origin import/restore and broad injected-HTML/direct-storage writer reviews remain OPEN and block any main release. No data schema change, no personal data involved.


## 2026-10-24 Beta7
LUM-BUG-030 Body/Protocols/Settings density improved as user-approved design candidate. 80/80 isolated fake-storage checks PASS, Safari NOT VERIFIED. Pre-existing weekly reorder referenced an undeclared inventory variable; candidate defines it locally, but real touch/keyboard persistence remains NOT TESTED. Critical photo-backed cross-origin restore, injection/security and demo isolation issues remain open until true device testing. No bugs silently closed.
