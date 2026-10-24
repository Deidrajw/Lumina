# Project State
Updated: 2026-10-24, following broad audit.
**App code baseline:** main `2e02f304dcbb29931d3468dbb51fdbbb2a3bf962`, v0.9.4. **Docs branch:** docs/project-governance-2026-10-24. **Deployment:** user confirmed https://lumina-9w6.pages.dev/ is deployed; independent live fetch/deployment SHA verification BLOCKED.
**No production code changed.** Audit report: `docs/AUDIT_2026-10-24.md`.
**Validated isolated:** five viewport widths, all core renderers, text symptom/concern/product workflows, supplement search, delayed detail edit, theme, Doctor Summary setup/review. **Failed isolated:** populated Vault Cleanup (_invSearchFocused undefined), ordinary modal Escape, unescaped stored HTML executing event. **Code-confirmed high risks:** photo import missing blob restoration, delete/cancel photo loss, Clear All leaves IDB, progress save ignoring errors, UTC date, demo low-level write boundary and sensitive console logs.
**Not tested:** live Cloudflare, Safari, real IndexedDB photo storage/clean restore, PDF/share, reorder/touch.
**Next EXACT step:** Review audit priorities and docs PR #1; approve P0 data-safe fixes; create feature branch from refreshed main; test all image lifecycle paths on a real origin before deploying. Do not alter main without approval.

---
# Project State
Updated 2026-10-24. Repo: Deidrajw/Lumina; main branch contains root `index.html`, v0.9.4. Cloudflare Pages intended; connection and live URL unverified. No app code updates during governance setup.

### Confirmed in latest HTML
Standalone HTML/CSS/JS. Main areas: Today, Body, Protocols, Vault, Insights and Settings. Current fonts: Instrument Serif / Manrope. localStorage stores most records; IndexedDB holds attached photo blobs; legacy photo migration code exists. Sample preview is designed to be isolated (QA required). Doctor Summary and export workflows exist (QA required).

### Source discrepancies
Older Claude context mentions DM Serif/Inter, purely localStorage, and a v0.12 historic roadmap; actual current code takes precedence. Avoid replacing current v0.9.4 with those concepts.

### Important blockers
Photo JSON export includes `_photoBlobs`, but current `importData()` does not restore them; do not move an active user's browser-data origin until round-trip tested. See KNOWN_BUGS.

### Next priorities
1. Review documentation PR; do not alter index.html.
2. Plan Cloudflare Git connection with main production and PR previews.
3. Prepare full functional and UI/UX audit.
4. Address data portability and critical bugs on approved feature branches.

At each session end append verified HEAD/branch, PR, outcomes, blockers and next step.