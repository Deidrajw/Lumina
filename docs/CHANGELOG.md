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
