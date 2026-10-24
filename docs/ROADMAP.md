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
