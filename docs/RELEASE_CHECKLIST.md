# Release Checklist
Version: __ | date: __ | branch/PR: __ | commit: __ | Cloudflare deployment: __
- [ ] Requirements/acceptance and regression risks documented
- [ ] Latest main consulted; no feature/data loss or silent redesign
- [ ] Tests: personal/empty/demo, iPhone Safari, light/dark, overlays, navigation, core CRUD
- [ ] Test photos, search/edit, protocols, doctor summary, storage quota
- [ ] FULL export/import RESTORE tested on another origin including IndexedDB photos
- [ ] Preview and standalone HTML ready
- [ ] Versioned ZIP includes root index.html
- [ ] Changelog, requirement statuses, bugs, QA, state and continuity updated
- [ ] Public diff has no private health data/secrets
- [ ] PR preview checked, release approved, production URL actually verified
- [ ] Rollback commit recorded and user data safe
Decision GO/NO-GO: __ | evidence: __

## Phase B v0.9.5-beta.2 release gate
- [x] Git branch candidate, beta version and root index.html
- [x] Embedded JavaScript syntax validation
- [x] 13/13 isolated Chromium Phase B tests PASS
- [x] 17/17 simulated Phase A photo/data regressions PASS
- [ ] Security review for ALL remaining stored-text HTML and imported attributes
- [ ] Complete read/write isolation across demo preview, photos, settings, onboarding and migrations
- [ ] Real iPhone Safari and actual Cloudflare preview URL/commit verified
- [ ] Real IndexedDB backup/restore and photo comparison across browser origins
- [ ] Full populated/empty and light/dark manual regression
- [ ] Explicit production merge/deploy approval
Current: NO GO for Cloudflare production. Rollback source main commit 2e02f304. Code rollback is not data recovery.


## v0.9.5-beta.3 GO/NO-GO
- [x] JS syntax validated, 16/16 isolated synthetic Chromium checks PASS, five viewport widths
- [x] Versioned root index.html, ZIP and fictional preview
- [ ] Real Cloudflare preview SHA / branch controls verified
- [ ] Actual iPhone Safari and genuine indexedDB cross-origin backup/restore
- [ ] Full escaped HTML sink and direct storage side-effect audit
- [ ] Full populated/empty, dark/light and doctor/photo regressions
- [ ] Overlay focus, outside tap and unsaved state recovery fully tested
- [ ] Explicit user approval for main deployment
NO-GO production; rollback code main 2e02f304 does not restore browser data.


## v0.9.5-beta.4 release checklist (2026-10-24)
- [x] Latest GitHub main/parent beta and continuity docs inspected
- [x] Root index.html source SHA verified after build
- [x] Standalone fictional-data preview, deployable ZIP, release notes, regression checklist
- [x] Focused 22/22 isolated Chromium fake-storage checks PASS, 320/375/390/393/430 px
- [x] JavaScript syntax PASS, no uncaught errors observed in focused QA
- [ ] Cloudflare beta.4 preview URL/commit SHA confirmed
- [ ] Actual Safari add/edit/cancel photo and clean origin backup restore including IndexedDB
- [ ] All remaining HTML injection sinks and direct storage writers audited
- [ ] Full app manual functional UI and accessibility regression, light/dark, empty/populated, doctor export, camera
- [ ] Explicit production merge/deploy approval
**NO-GO for main** until the above; code rollback does not restore browser data.


## v0.9.5-beta.5 — Accessibility-focused update GO/NO-GO (2026-10-24)
- [x] GitHub latest main + beta source/continuity checked
- [x] Root index.html candidate, standalone fictional preview and deployable ZIP
- [x] Embedded JavaScript syntax PASS
- [x] Isolated Chromium all 6 panels × 320/375/390/393/430px × light/dark = 60/60 PASS
- [x] Visual before/after and interactive six-screen proposed concept produced
- [ ] Real Cloudflare beta.5 deployment SHA confirmed
- [ ] Actual iPhone Safari/VoiceOver/keyboard/zoom/safe-area testing
- [ ] Clean-origin photo backed JSON import/export and IDB persistence test, including errors
- [ ] Full security/UI/UX and data isolation functional regression
- [ ] Approved direction for substantial visual redesign and separate implementation QA
- [ ] Explicit merge/deploy authorization
**NO GO for main**; rollback code beta4 commit d33e0ce, production main 2e02f304; code rollback cannot recover deleted records.


## v0.9.5-beta.6 review release gates, 2026-10-24
- [x] Latest repo main/parent beta HEAD and continuity read
- [x] Root index.html deployable ZIP and fictional standalone preview produced
- [x] 69/69 isolated Chromium screen/interaction checks PASS, JavaScript syntax PASS
- [x] Requirements LUM-022/023/024 implemented beta, LUM-025 approved for next batch
- [ ] Cloudflare feature branch preview commit verification and iPhone Safari user review
- [ ] Full photo-backed clean-origin export/import and refresh using actual IndexedDB
- [ ] All core CRUD/error/demo/empty flows and linked views across screens
- [ ] VoiceOver, large text, keyboard and mobile safe area review
- [ ] Comprehensive injection and data-write-boundary audit
- [ ] User explicitly approves merge/deploy production
**NO-GO for production** until above. Rollback beta5 a7d9ae2, production main 2e02f304. Code rollback does not restore lost browser data.


## Beta7 GO/NO-GO — 2026-10-24
- [x] Latest GitHub Beta6 source, history and pending bugs reviewed
- [x] Beta7 complete root index.html, fictional HTML preview, ZIP, notes, screenshots
- [x] 80/80 isolated Chromium fake-storage checks PASS; JS syntax PASS
- [ ] Cloudflare Beta7 preview SHA verified and physical iPhone Safari QA
- [ ] Real clean-origin JSON/IndexedDB photo restore including after refresh and failure recovery
- [ ] Full Body/Protocols/Settings CRUD, weekly reorder persistence, Rx/supplement and doctor report regression
- [ ] VoiceOver/safe-area/zoom/keyboard, quota, data privacy, injection and mutator review
- [ ] Separate explicit authorization to merge/deploy main
NO-GO production. Rollback candidate Beta6 32e66d5; main 2e02f304; code rollback does not restore browser data.


## Beta8 GO/NO-GO — 2026-10-24
- [x] Latest GitHub branch and project continuity inspected; Beta7 app blob verified exact from deployable package
- [x] Doctor Summary selection, result and presentation escaped; numeric handler events
- [x] Current-origin photo readiness check + v2 complete JSON validation/empty checks fallback
- [x] Syntax and 27/27 automated synthetic Chromium checks PASS, 320–430px both themes
- [x] Versioned root index.html, ZIP, fictional preview, QA checklist, release notes, screenshot
- [ ] Cloudflare beta8 preview SHA and actual iPhone Safari check
- [ ] Real IDB photo save/export, separate HTTPS origin import, refresh and verify 4 categories with photo ID/bytes
- [ ] Real quota, missing blob, failed write + backup rollback on Safari
- [ ] Full doctor report/copy/share, editable imported records and all app regression
- [ ] Comprehensive security/VoiceOver, origin migration and explicit user production approval
**NO GO for main** until these complete. Code rollback previous Beta7 b48dca8 / production 2e02f304, which cannot restore lost browser data.


## Beta9 GO/NO-GO (2026-10-24)
- [x] Latest GitHub HEAD/code + governance docs refreshed; branch based on Beta8 source
- [x] Full root index.html beta9, fictional preview, screenshots, changelog/QA/tester notes and ZIP
- [x] Category/Form combined filtering plus reset/type/presets/option safety tested in isolated Chromium
- [x] Cleanup preflight Cancel/Apply/session Undo, stale state/failed simulated save, read-only sample tests
- [x] JavaScript syntax and 105/105 isolated Chromium checks PASS on six tabs/five widths/two themes
- [ ] Cloudflare preview SHA and physical iPhone Safari Beta9 tested
- [ ] Real clean-origin JSON/IndexedDB photo save/export/import after refresh, including quota and rollback
- [ ] 20+ products, all Vault forms/filtered no-result/long label/VoiceOver state on iPhone
- [ ] All CRUD, Doctor Summary, overlays, settings, privacy and security regression
- [ ] Separate explicit approval to merge or deploy production main
**NO GO** until release blockers pass. Source fallback Beta8 1ee253d; production main 2e02f304. Code rollback cannot restore browser records.
