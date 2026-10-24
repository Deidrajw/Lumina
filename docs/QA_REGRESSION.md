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
