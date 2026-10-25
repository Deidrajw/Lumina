# Roadmap
1. **Foundation:** docs/continuity + GitHub workflow; Cloudflare plan; robust cross-domain backups (including photos).
2. **Audit and stabilization:** full UI/UX and function audit. Prioritize photo save/restore, supplement search, detail edit return, overlays, Smart Capture truthful behavior, protocol reorder, safe areas and demo safety.
3. **Polish:** visual consistency, useful insights with evidence and caveats, better doctor summaries and linked record views.
4. **Later (not yet approved):** richer product-centered patterns, before/after comparisons, secure OCR, optional sync, PWA/native iOS/Android, push reminders and integrations.
Do not expand major features before stabilizing core flows.
## 2026-10-24 audit-based order (pending approval)
1. P0 photo storage lifecycle, backup/restore, clear-all + quota correctness (LUM-008/009/010/011).
2. P1 Vault cleanup, safe HTML rendering, timezone dates and demo write boundary (LUM-012/013/014/015).
3. Real iPhone/Safari functional regression: photo save, search edit, reorder, physician reports and QR/download flows.
4. P2 visual polish: contrast, touch sizes, reliable modal escape, honest Smart Capture, current version banner, Today/Insights density.
5. Cloudflare build SHA/preview/rollback verification and user-approved release.


## Phase B status 2026-10-24
Beta v0.9.5-beta.2 implements selected Cleanup, date, demo isolation and output escaping fixes. NOT release-ready: broader HTML/handler security review, all storage mutators, actual iPhone Safari and genuine photo backup restoration remain. Preserve v0.9.4 main until approved. Next after stabilization: Phase C overlay Escape and safe-area polish, user-approved grouped cards/accordion density improvements, honest Smart Capture wording.


## Beta.3 focus (2026-10-24)
Escape stack, honest Smart Capture, doctor-print output safety and sample preview setting isolation implemented as candidate; real-browser/IDB/Safari QA and full security audit still gate shipping. Next design-only Phase C concepts after stable release: reduce Today and Insights density with user-approved previews, improve touch targets, colour contrast and focus states.


## Phase D candidate 2026-10-24
Beta.4 targets the Vault JSON import bypass, unsafe product/detail/search/CSV text display and false success states. Built and isolated-tested but not deployed to main. Next production gates: Cloudflare beta.4 preview SHA + user iPhone Safari photo cancel/save/refresh; complete photo-backed backup clean-origin restore; exhaustive HTML, inline handler and direct-write audit; regression across all sections. After baseline release and approval: Today/Insights grouped density redesign concepts.


## Phase E UI/UX audit, beta.5, 2026-10-24
**Implemented candidate:** nonstructural accessibility/contrast/touch/focus/zoom improvements LUM-021 on separate PR and Cloudflare preview when confirmed.
**Design proposed only:** interactive six-screen concept studio (docs/prototypes/UIUX_Concept_Studio.html) for LUM-022–025 Today, Body, Protocols, Vault, Insights, Settings. Preserve original data/functionality; substantial redesign requires user approval after comparison.
**Next:** actual iPhone Safari, VoiceOver/200% zoom and synthetic photo restore/rollback. Full security and UX regression and documented approval before production release; add meaningful performance baseline LCP/INP/CLS, not inferred values.


## User approved UI/UX concept — Phase 1 implementation, 2026-10-24
**Implemented beta6:** Today, Vault and Insights (LUM-022/023/024) progressive hierarchy and evidence, original data contracts and feature paths intact, real Safari review pending.
**Approved design, next batch:** Body task-first logging/filters, Protocols clearer steps and non-drag reorder, Settings prominent backup/restore and professional reports (LUM-025). Stage and test before implementation.
**Release gates:** real Safari + clean-origin photo backup restore, broad security, all-screen regression, explicit production authorization. Main remains v0.9.4 until release.


## 2026-10-24 UX design implementation progress
Beta6 candidate implemented Today/Vault/Insights; Beta7 candidate now implemented approved Body/Protocols/Settings. Both stacked in feature branches and not deployed to production main. Next verify physical iPhone Safari, photo-complete clean-origin IndexedDB restore, all functional CRUD, screen-reader/security/error tests, then separate production merge approval. No new feature category before stability.


## 2026-10-24 — scorecard-directed sequence
57 graded Beta7 pages/subflows (see AUDIT_PAGE_GRADES_2026-10-24.md). P0 first: clean origin IDB photos+JSON restore validation, sanitize Doctor Summary confirmation/result. P1: Vault independent form/category filters, weekly reorder persistence in Safari, Data Cleanup bulk-change preview, full modal/focus/VoiceOver regression and transparent Insights evidence. Next: user-measured task completion on iPhone and compare scores after verified change. Main remains v0.9.4; audit not a production release.


## 2026-10-24 Beta8 repair progress
Doctor Summary text safety + current-origin photo readiness check and stricter backup validation implemented Beta8 candidate. Next gating task: real iPhone Safari fresh HTTPS-origin export/import/refresh of four photo categories with recovery, then full regressions. After real data protection verification address LUM-030 Vault Form/Category filter, LUM-031 bulk cleanup confirmation and test Doctor Summary copy/share accessibility. Continue page grading with measured tests, not cosmetic inflation. No production release without approval.


## 2026-10-24 Beta9 and next release gate
LUM-030 filter collision and LUM-031 Data Cleanup bulk safety are IMPLEMENTED Beta9 candidates, tested in isolated Chromium. Current P0 highest priority remains full real HTTPS iPhone Safari export/restore of photos with IndexedDB after refresh. Then verify Vault search/edit, form/category/reset, cleanup preview/cancel/undo/failed writes on device, VoiceOver and full app security regression before production release. Continue to regrade affected surfaces only after verified user tasks. Main remains v0.9.4.


## 2026-10-24 Beta10 P0 test assistance
Implemented candidate LUM-033 read-only current-origin match of original backup records and photo bytes; this resolves lack of a post-restore comparison UI, but does NOT verify actual Safari portability. Highest next priority remains actual on-device photo-backed clean HTTPS-origin export/import/refresh and match with this tool, followed by real quota/rollback/CRUD and privacy/security audit. Maintain production main v0.9.4 until full regression and explicit release consent.


## 2026-10-25 Beta11
LUM-034 backup integrity strict read candidate implemented and isolated-tested, prior Beta10 restore verification plus Beta9 Vault safety retained. Next priority actual iPhone Safari cross-origin photo restoration and complete failed-write/rollback checks using fictional data. Then systematic direct-storage and innerHTML audit, full per-screen UX regression, VoiceOver and user-approved production merge. Current main v0.9.4 unchanged.
