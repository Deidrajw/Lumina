# QA Regression Matrix
Results: NOT TESTED | PASS MANUAL | PASS AUTOMATED | FAIL | BLOCKED; each needs date, device, commit, tester/evidence.

Widths: 320, 375, 390, 393, 430px; actual iPhone Safari, desktop keyboard; dark/light; empty/personal/demo sample.
- [ ] Start fresh, onboarding, optional isolated demo mode, safe exit; no personal writes
- [ ] Today progress, concerns, alerts, reminders; bottom content accessible
- [ ] Symptom/concern add, edit, save with and without photos; refresh
- [ ] Skin logs, Rx check-ins, progress photo viewer exit via close/back/Escape
- [ ] Vault product create/edit/archive/delete; linked records remain consistent
- [ ] Vault and supplement picker search with results/no results
- [ ] Search -> product detail -> edit -> save/cancel -> expected return
- [ ] Protocol add/edit/complete/skip/reorder and scheduled day filtering
- [ ] Photo capture/upload/manual and honest no-OCR fallback
- [ ] Insights date filters, plain-language caveats, related entries
- [ ] Doctor Summary current/custom selection, doctor view, export/copy/share
- [ ] JSON export + CLEAN ORIGIN import restores all fields AND photos
- [ ] storage quota/permissions, missing linked item, cancel paths and empty states
- [ ] Clear data resets intended localStorage and IndexedDB records
- [ ] All overlays close, scroll, safe areas, keyboard and focus states
- [ ] No undefined handlers or unhandled exceptions

Run record: date | version+SHA | environment | case | result | evidence | blocker.
## 2026-10-24 Audit run (no app patch)
**Test environment:** Chromium page.set_content offline; mocked localStorage; fictional records; NOT live Cloudflare or actual IndexedDB.
- PASS (automated isolated): Node JS syntax; 320/375/390/393/430px empty core renderer navigation/no horizontal overflow; fictional symptom create/edit; concern create/cancel; Vault product create; supplement search; product-detail edit/save after asynchronous return; theme toggle; Doctor Summary setup and selection; backdrop click; sample UI blocks symptom write.
- FAIL (automated isolated): populated Vault Data Cleanup undefined _invSearchFocused; Escape normal symptom modal not closed; user-provided HTML field evaluated as executable markup.
- PASS with caveat: fictional populated subview sweep of Body 5, Protocols 6, Vault 4/5, Insights 4, Settings.
- NOT TESTED: real IndexedDB photo lifecycle, cancel restore, quota, fresh-origin JSON restore, actual iPhone Safari, print/share/PDF, touch reorder, full global search-to-edit entry, large datasets.
- BLOCKED: live Cloudflare URL fetch/build SHA verification.
- Reusable evidence available in audit report; verify on real browser environment before any release status becomes Verified.

## Phase A v0.9.5-beta.1 — 2026-10-24
**PASS automated, controlled simulated storage:** 17/17 checks in Chromium with fake localStorage/IDB transactions: add photo fixture; Cancel preservation; draft cleanup; committed removal; export JSON; clean browser-context import; missing image validation; injection of storage write failure+rollback; progress photo storage/error draft; clear-all simulation; no overflow through 320/375/390/393/430px major tabs. JS syntax passed Node check.
**NOT TESTED/BLOCKED:** real-origin IndexedDB, iPhone Safari, actual separate-domain backup migration, quota, permissions, real camera, OS share, full screen-by-screen regression, Cloudflare preview deployment verification. DO NOT label production Verified. [Acceptance details](PHASE_A_DATA_INTEGRITY_2026-10-24.md).


## Phase B beta.2 test results — 2026-10-24
PASS automated isolated Chromium with mock localStorage and fictional data: 13/13 focused checks — Vault Cleanup populated, injected HTML literal display in Symptoms/Concerns/Vault/Cleanup/Timeline, Today/Insights cross-tab, raw saved strings unchanged, Toronto date parsing, symptom save, sample preview record and photo write isolation.
PASS automated simulated-storage regressions: Phase A 17/17 cases; basic navigation at 320,375,390,393,430px. PASS embedded JavaScript syntax validation.
NOT TESTED: actual iPhone Safari; genuine IndexedDB photo persistence and clean-origin restore; live Cloudflare preview/deployed SHA; exhaustive dangerous HTML sinks, remaining direct writes, legacy date DST, full doctor/share/overlay flows.
Status: beta candidate / NO GO production until real testing and approval.


## 2026-10-24 beta.3 isolated test results
PASS automated Chromium with fictional data and mocked localStorage (16/16): Escape symptom sheet, confirmation Cancel, product behind sheet, photo sheet, Smart Capture no OCR overpromise, hostile text in recent captures, PDF export escaping concern/symptom/prescription/supplement, demo theme/onboarding/profile/version/dev flags non-persistence, demo central save denied, no horizontal overflow on five tabs at 320/375/390/393/430px. PASS Node JS syntax. No page errors in isolated run. BLOCKED local HTTP/HTTPS browser origin (`ERR_BLOCKED_BY_ADMINISTRATOR`), so true IndexedDB cross-origin restore not tested. NOT TESTED real iPhone Safari, full doctor/share, all HTML sinks, all direct storage writers, keyboard focus and full regression. Current release decision NO-GO.


## Phase D v0.9.5-beta.4 — 2026-10-24
PASS (automated isolated Chromium, fictional/malicious fixtures and mocked localStorage): 22/22 checks. Global-search renderer (test host) safe text + product click; product detail values, journal, linked symptoms/concerns and picker safe; Rx custom effects safe; no HTML event execution; Vault JSON file uses actual FileReader and raises shared Restore confirmation without overwriting; CSV header and preview displays escaped strings; preview mode blocks CSV write; UI version current; 320, 375, 390, 393 and 430px no horizontal overflow. PASS node --check; no uncaught page errors in focused tests.
NOT TESTED: live Cloudflare beta.4 preview, actual Safari photo save/cancel/refresh and complete JSON restore on clean browser origin; all product/search screens/handlers and direct-write paths; all theme/device combinations and full app regression.
BLOCKED local origin: Chrome automation disallows localhost navigation (ERR_BLOCKED_BY_ADMINISTRATOR), so IndexedDB real-origin testing unavailable here. User independently confirmed prior beta.3 preview opens in iPhone Safari, not a full pass for this beta.
No production validation. See docs/PHASE_D_IMPORT_DISPLAY_SAFETY_2026-10-24.md and artifacts QA_CHECKLIST.md.


## 2026-10-24 v0.9.5-beta.5 accessibility foundation
PASS automated isolated Chromium, fictional Sample Preview/localStorage mock: 60/60 screen checks (Today/Body/Protocols/Vault/Insights/Settings x 320/375/390/393/430px x dark/light). Current nav aria-current tracks selected primary tab, no misleading nav selection in Settings; labels 11px; Settings control 44px; no horizontal overflow or page exceptions. Embedded JavaScript Node syntax PASS.
PASS calculated: dark tertiary on card #1c1925 ~5.37:1 versus old 2.75:1; light tertiary on white ~5.82:1 versus old 2.93:1. Flat token pairs do not prove all overlays/translucency meet WCAG AA.
PASS automated isolated design concept: six mock tabs work, fake Vault search filters, theme switch works; zero page exceptions.
NOT TESTED actual beta.5 Cloudflare deployment SHA, iPhone Safari/VoiceOver, CRUD/photo, cross-origin IndexedDB backup, 200% zoom, full keyboard focus, data integrity/security and LCP/INP/CLS. No production release certification. See docs/AUDIT_UIUX_FULL_2026-10-24.md.


## v0.9.5-beta.6 test evidence — 2026-10-24
PASS isolated Chromium (fictional mocked localStorage): 60 screen renders = 6 main sections × 320/375/390/393/430px × dark/light, with no document horizontal overflow or uncaught page errors. 9 more PASS isolated cases: populated Vault group/review, expandable Unopened with aria-expanded, Vault search, Insights evidence/context details and retained expanded state, Today check-in and bounded total, quick symptom editor and history expansion. PASS JS Node syntax.
NOT TESTED real Safari Beta 6, full create/read/edit/save/cancel/delete flows and photos, clean-origin IndexedDB photo restore, import failure/quotas, VoiceOver/zoom, full security writers/HTML audit, full doctor reports and real CWV performance. Production NO-GO pending QA and approval. Artifacts include QA_CHECKLIST.md and JSON synthetic test evidence in ZIP.
