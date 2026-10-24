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
