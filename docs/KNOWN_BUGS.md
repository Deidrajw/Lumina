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
