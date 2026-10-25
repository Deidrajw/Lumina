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


## Beta7 — 2026-10-24
PASS automated isolated Chromium with synthetic in-memory localStorage: six sections × 320/375/390/393/430px × light/dark = 60 screen cases without page errors/overflow. PASS 20 focused cases: Body symptom/concern/skin original editor opens, filter disclosure persists on rerender, Rx/Progress More tabs; Protocols scheduled count, Show all/Reorder controls, Week/Supplements transitions, populated AM count; Settings doctor summary/import and collapsed setup/reset actions available. Embedded JS syntax Node PASS. NOT TESTED physical Safari/VoiceOver, real IndexedDB clean HTTPS-origin JSON/photo roundtrip, full linked CRUD, quota/errors, doctor report/share, comprehensive injection/write boundary/security and keyboard focus. NO GO main.


## 2026-10-24 — Every-page grade audit (no app patch)
**PASS automated current:** 37/37 isolated Chromium render/open smoke (22 navigation/subviews, 15 modal opens), 390px dark, fake localStorage, fictional Sample Preview; no uncaught page errors or captured Display error. **PASS prior documentation, NOT rerun here:** 80/80 Beta7 six-screen/width/theme + 20 interaction suite.
**PASS automated gradebook preview:** 57 static cards rendered; P0 filter returned 10; text search narrowed matches; no script exceptions in set_content. file:/// navigation blocked by browser, used set_content instead.
**NOT TESTED:** real Safari/VoiceOver full app, actual IndexedDB clean-origin photo restore and error recovery, full CRUD, doctor report unsafe HTML scenario, Vault form filter end-to-end, quota, performance and comprehensive mutators.
**Report:** docs/AUDIT_PAGE_GRADES_2026-10-24.md. Grading numbers are heuristic opinion, not measured task completion, and must not turn into Verified bug statuses.


## v0.9.5-beta.8 focused test run — 2026-10-24
PASS automated isolated headless Chromium, synthetic private-free data, localStorage and IndexedDB photo functions mocked: **27/27**. Three Doctor Summary views resist synthetic img.onerror payload; checkbox state works for malicious ID, raw copy text intact; four linked categories (symptom, concern, product, progress) found, existing/missing photo readiness correctly reported; invalid v2 incomplete backup rejected, legacy partial remains valid, missing payload rejected; export four blobs and full section list; incomplete export blocked; synthetic restore and injected quota write rollback; empty new install checks key exports valid {}; Settings 320/375/390/393/430 px both themes no overflow. PASS JS Node syntax; zero page errors.
**BLOCKED:** actual IndexedDB in real browser HTTP/HTTPS origin (headless environment blocks navigation). **NOT TESTED:** physical iPhone Safari, true download then clean-origin import with blobs/IDs after refresh; actual quota/recovery, full Doctor Share/print, all app features and exhaustive HTML writer security, VoiceOver. Passing mocks cannot verify real photo portability. See BETA8_BACKUP_DOCTOR_SAFETY_2026-10-24.md and beta8 ZIP QA_CHECKLIST.


## 2026-10-24 v0.9.5-beta.9
PASS automated isolated Chromium, fictional in-memory localStorage: 105/105 checks. 45 targeted Vault form/category combined & single-state filtering, reset/type/preset/Rx, safe option rendering, preflight count/names, Cancel no writes, Apply only selected fields, Undo without replacing unrelated edits, excluded archived/finished, stale preview abort, failed mock save and sample preview no-write; 60 screen/width/theme checks (6 sections x 320,375,390,393,430 x light/dark). PASS Node JS syntax, no uncaught browser page errors. Test script and QA_RESULTS.json are in the local package; no private records.
NOT TESTED physical iPhone Safari, true origin-specific localStorage quota errors, real IndexedDB photo backup/clean-origin restore, full application doctor/form/import/overlay regression, screen-reader focus, all HTML sinks and mutation paths. Production release blocked pending P0 photo test and explicit approval.


## 2026-10-24 Beta10 verified-backup feature
**PASS automated isolated Chromium 77/77:** file input and FileReader read original JSON, 13/13 saved sections plus four mocked linked-photo payloads byte match, no record-key writes, changed symptom section detected, one missing photo and one-byte mismatch detected, empty photo set & legacy partial not certified, incomplete payload rejected, Sample Preview denied; 60 screen checks (Today/Body/Protocols/Vault/Insights/Settings × 320/375/390/393/430 widths × both themes) without unhandled errors or overflow. PASS Node JS syntax. Test uses in-memory localStorage and mocked luminaGetPhoto, **NOT real IndexedDB**. One async version-seen preference write on startup is unrelated; verify file selection left all 13 record keys unchanged.
**BLOCKED actual origin:** Chromium localhost and placeholder HTTPS navigation denied ERR_BLOCKED_BY_ADMINISTRATOR. Therefore real cross-origin IndexedDB photo restore **NOT TESTED**. **NOT TESTED:** actual Safari file picker, clean-origin restore after refresh, image re-opening, real quota, Doctor reports, comprehensive app/safety regression and VoiceOver.
Release NO-GO pending user-run fictional Safari test on two different Cloudflare hostnames, along with whole-app QA and explicit production authorization.


## 2026-10-25 Beta11 strict backup reads
PASS automated, isolated Chromium 90/90: strict 13-section source reader on valid/absent/wrong type/JSON malformed, denied storage, export blocked while raw bytes remain untouched, photo readiness detects corrupt source, valid first-install 13-section export, destination missing/corrupt checks fails verification, mocked photo-backed exact match rejected if one record section corrupt. Plus 60 screen/width/theme navigation checks (Today/Body/Protocols/Vault/Insights/Settings x 320/375/390/393/430 x light/dark) with no uncaught page exceptions or document overflow. PASS embedded JS node --check. Only fictional fake localStorage and a mock photo Map used.
BLOCKED Chromium HTTPS-origin navigation (ERR_BLOCKED_BY_ADMINISTRATOR), so no genuine browser IndexedDB test despite trying to intercept requests.
NOT TESTED real iPhone Safari, cross-origin full photo JSON export/import/refresh, actual quota/perms/rollback, VoiceOver, complete linked CRUD, doctor reports and global security. Strict helper blocks bad data; it cannot repair it. Release remains NO-GO main.


## Beta11 post-package visual check (2026-10-25)
After detecting stale Settings version fallback label, updated footer to display LUMINA_VERSION. Re-ran full 90/90 isolated Chromium fake-store suite and Node syntax PASS against final code (Git blob 4f80428d9c989deaf7b6ded50d569b55c246f3f1). Screen capture confirms Settings now displays v0.9.5-beta.11. No real Safari or origin-specific IndexedDB checks were added.
