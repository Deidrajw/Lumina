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