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
