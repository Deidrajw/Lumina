# Changelog
## Unreleased — documentation/governance setup (2026-10-24)
- Added project instructions, continuity records, requirements, bugs, QA, architecture, design, roadmap, decisions and Cloudflare deployment plan.
- No index.html update. Current app stays v0.9.4. No user data change. No Cloudflare deployment.
- Audit flag: photo restore with JSON backup needs verification/repair.

## Current observed app v0.9.4
Confirmed in current index.html; existing body, vault, protocols, insights, settings, IndexedDB photos and demo preview. Detailed provenance of individual v0.9.4 features not fully reconstructed.

## Historical context
Older Claude combined changelog uses conceptual v0.1–v0.12 milestones. These cannot be assumed to match deployed code release tags. Preserve history, but version against the current executable source.

Future entry template: date | version | PR/commit | added/changed/fixed | data impact | tests | known issues | rollback.
## v0.9.5-beta.1 — unreleased candidate (2026-10-24)
- Staged symptom/concern photo edits, safe Cancel, clean new Vault drafts.
- Export all referenced IndexedDB photo blobs or block incomplete backup; validate photo-complete JSON import, explicit replace confirmation, best-effort rollback on errors.
- New progress photos stored in IDB; failed saves leave draft and form; old base64 progress records still visible.
- Clear All wipes Lumina localStorage and image store; Onboarding Fresh respects existing data.
- Capture-to-Vault product photo moved to IDB on save; removed sensitive log; Settings copy and beta version updated.
- **Data:** backward-compatible reads; new progress photo metadata `photoId`. **QA:** 17/17 simulated Chromium checks + Node syntax; real Safari/Cloudflare/cross-origin storage NOT TESTED. **Deploy:** NOT MERGED or DEPLOYED TO MAIN.


## v0.9.5-beta.2 — 2026-10-24 — UNRELEASED
Added safe display escaping for stored strings in tested primary Today/Body/Vault/Insights/Timeline views; browser-local date helper.
Fixed Vault Cleanup populated ReferenceError, selected HTML event injection exposures, and known sample-mode central storage write boundary.
Changed sample greeting to Sample User and denied IndexedDB photo mutation during Sample Preview. Phase A photo safeguards preserved.
No schema migration; existing UTC-derived dates remain stored, new dates local. No production deployment.
Tests: 13/13 focused isolated Chromium + 17/17 Phase A simulated regression PASS; genuine iPhone Safari/Cloudflare/real cross-origin photo restore NOT TESTED. Broader security review remains open.


## v0.9.5-beta.3 — UNRELEASED (2026-10-24)
Escape closes uppermost modal/confirmation before underlying product page, following existing Cancel cleanup. Smart Capture clarifies OCR not connected and manual label entry; recent capture data escaped. Printable Doctor Summary now escapes dynamic fields and provides blocked-popup feedback. Sample Preview doesn't persist theme/onboarding profile/goals/completion/version-seen/developer flags. No schema migration, no private records accessed. 16/16 PASS isolated Chromium/fictional mock storage + Node syntax; real IndexedDB, Safari and Cloudflare preview NOT TESTED. No merge to main.


## v0.9.5-beta.4 — Unreleased candidate, 2026-10-24
- Fixed Vault JSON import bypassing validated, photo-complete backup restore and explicit replace confirmation; Settings and Vault now call the same restore flow.
- Safe DOM-based rendering for dormant global-search results and click handling; escaped product detail, journal, linked symptom/concern, CSV mapping/preview and Rx custom effects.
- CSV import refuses read-only preview and does not announce success after failed save; Home Screen build label dynamically uses current version; developer reset controls respect Sample Preview; activity seed marker only saved after successful log save.
- No data migration or schema change; raw stored user text untouched.
- QA: 22/22 focused isolated Chromium PASS, JS syntax PASS. Real iPhone Safari photo/backup, actual Cloudflare beta.4 preview build, entire security/mutator audit, and full E2E NOT TESTED. Versioned deployable ZIP and fictional read-only preview available. Production main v0.9.4 unchanged.


## v0.9.5-beta.5 — UI/UX foundation, UNRELEASED (2026-10-24)
- Dark/light tertiary and dark secondary text contrast improved; readable navigation and section/form headings.
- Settings icon, selected tabs and small actions have larger tap targets; iPhone form text 16px; user zoom permitted.
- Keyboard focus-visible and reduced-motion support; nav and Settings accessibility names and aria-current active page.
- No migration, new features, removed screens or IA changes. Beta.4 changelog history preserved.
- Separate fictional six-screen interactive proposed design studio available for user review, not integrated.
- QA 60/60 isolated Chromium screen/theme/width checks PASS, JS syntax PASS. Actual Safari/VoiceOver/photo restore/full regression NOT TESTED. Production main remains v0.9.4.


## v0.9.5-beta.6 — Approved UX Phase 1, unreleased (2026-10-24)
- Today: primary skin check-in, quick symptom/routines actions, needs-attention and concerns visible, additional symptom/history details collapsed but available; routine total uses completed/scheduled + daily log, no-schedule shown as dash.
- Vault: in-use/available summary, quick needs-review route, collapsible existing alerts and secondary inventory; accessible button group headings, existing search/filter/CRUD intact.
- Insights: lead with logged observation and timeframe/caveat; grouped supporting entries/category and extended skin/Rx sections without deleting historical views.
- Six-screen user-approved concept, Body/Protocols/Settings staged next. No schema/ID or photo storage changes, no migrations.
- **PASS isolated automated Chromium:** 69/69 across 5 widths/2 themes/six screens + 9 populated interactions; JS syntax PASS. **NOT TESTED:** actual iPhone Safari, fresh-origin JSON+photo restoration, full app security, VoiceOver and regression. No production main merge or deployment.


## v0.9.5-beta.7 — Approved UX Phase 2 (2026-10-24), UNRELEASED
- Body: quick Symptom, Concern and Skin Log; optional filter/sort disclosure and explicit history headings, all original tabs/forms.
- Protocols: scheduled/completed routine context and visible Show all/Reorder, aria-pressed, supported-mode disabling; weekly reorder inventory reference corrected.
- Settings: Professional Summaries separate from JSON Backup/Restore; local browser storage/replacement explanation; setup and destructive reset behind separate native disclosures, original controls retained.
- No schema/ID/migration/IDB photo changes; Beta6 features preserved. PASS 80/80 automated isolated Chromium (five widths/two themes and 20 interactions), Node JS syntax. NOT TESTED real iPhone Safari/photo restore/complete regression/security. No main merge or deployment.


## 2026-10-24 — documentation-only page grading audit
- No app code, data schema, production branch or Cloudflare deployment changed.
- Added 57-surface UI/UX grading report and separate project-management maturity assessment with P0/P1 requirements.
- Current QA 37 isolated render/open checks PASS; actual Safari, cross-origin IndexedDB restore, full security and functional regression remain NOT TESTED.


## v0.9.5-beta.8 — Doctor Summary & photo backup protection (2026-10-24) — unreleased beta
- Doctor Summary selection/confirm, generated result and presentation view safely render user/imported text; checkboxes use listeners and numeric indexes, not raw IDs inside inline JavaScript. Clipboard and share text unchanged.
- Settings Backup & Restore now offers Check saved photos: checks existence, nonzero size and MIME type for each linked symptom/concern/product/progress IDB photo on THIS ORIGIN; missing photos get warning. This does NOT verify a cross-origin restore.
- JSON export validates assembled full v2 file and refuses incomplete images; fresh install without checks data exports checks as {}; v2 import requires complete sections and nonempty image photo blobs before writes; legacy partial backup compatibility retained. Import confirmation displays section/photo counts.
- No changes to record schema/IDs, existing photo blobs, migrations or production main. PASS JS syntax, 27/27 isolated Chromium fake-storage tests. Physical Safari, real IDB clean-origin photo restore, quota and complete app QA NOT TESTED. NO GO production.


## v0.9.5-beta.9 — Vault filtering and safer cleanup (2026-10-24) — unreleased
- Vault: Category and Form independently filter Supplements and Rx; combined selections work; reset/type/preset clears stale form; filter counts accurate and filter options safely rendered.
- Data Cleanup: category suggestions and Mark Finished now show affected product count and names BEFORE any save, require approval; Save failures/stale records safely stop action; one in-session scoped Undo if affected fields not edited afterward; archived, Finished and Empty zero-qty products excluded. Suggestions use existing category taxonomy.
- No schema, ID, photo, backend or migration changes; no production deployment. 105/105 isolated automated Chromium tests PASS, JS syntax PASS. Real iPhone Safari, complete IndexedDB photo restore, VoiceOver and full security/CRUD NOT TESTED. NO-GO main.


## v0.9.5-beta.10 — Read-only Restored Backup Verification (2026-10-24) — UNRELEASED
- Settings > Backup & Restore adds Verify restored backup: select the previously exported original JSON AFTER restoring to a different browser hostname. Reads but never rewrites JSON, app records or IndexedDB images.
- Compares all stored sections against the backup with stable JSON object key order; each linked photo compared on MIME type, byte length and byte-for-byte contents. Errors/missing/different records explained; zero photos and partial legacy JSON cannot earn a complete photo PASS.
- No schema, IDs, migrations, photo processing, backend/cloud writes, or data deletions. Beta9 filters and cleanup retained.
- PASS JS syntax and 77/77 isolated Chromium synthetic fake-storage checks, all six tabs × 320/375/390/393/430px × dark/light plus 17 functional/edge checks. NOT TESTED real physical Safari, true IDB clean-origin import/refresh, quota, VoiceOver/whole app regression. NO production merge.


## v0.9.5-beta.11 — Strict Backup Read Integrity (2026-10-24), unmerged candidate
- New backup-only strict section reader refuses malformed browser JSON, wrong saved-data section types and missing restored sections. Backup export now fails visibly instead of exporting fallback empties; linked-photo preflight refuses to claim checks if stored reference sections are unreadable; original JSON vs destination verifier marks missing/corrupt sections as differing.
- A genuinely absent new-install key may still export an appropriate empty list / checks object; only post-import verification requires all keys actually saved.
- No record-schema migration, ID/photo modifications, automated repair or production deploy. PASS 16/16 focused isolated Chromium tests with mock localStorage and embedded JS syntax. Full app page test timed out; actual Safari/IDB clean-origin restore and full app regression NOT TESTED.
