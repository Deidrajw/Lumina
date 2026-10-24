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
