# Lumina Phase A — Photo and Data Protection Beta
**Candidate:** v0.9.5-beta.1, build 2026.10.24.phase-a.1
**Date:** October 24, 2026
**Base production:** main 2e02f304, v0.9.4, unchanged
**Source branch:** fix/photo-data-integrity-v0.9.5-beta.1, stacked on docs/project-governance-2026-10-24
**Status:** Implemented in beta; NOT VERIFIED for production; NOT deployed to main.

## Scope (LUM-008, 009, 010, 011)
- Symptom and concern photo removals stage until Save; Cancel preserves existing blobs and cleans newly added draft photos. Vault photo drafts also clean on Cancel.
- Portable JSON export includes referenced IndexedDB blobs from symptoms, concerns, products and progress photos. Missing blob blocks incomplete export.
- Import validates completeness before writing and asks user to approve REPLACE; stages blobs and attempts to roll back keys/blob overwrites if a write fails.
- New progress photos use compressed IndexedDB blobs + lightweight record metadata. Legacy base64 progress photos still render. Failed save retains draft form.
- Clear All deletes Lumina localStorage and IndexedDB photo store for current origin; explicit confirmation. Onboarding Start Fresh no longer silently wipes existing records.
- Product images from Smart Capture are converted to IndexedDB on save. Removed product-object logging; Settings backup/reset copy clarified.
- Beta app version/changelog UI updated.

## Data and compatibility
No automatic destructive migration on page load; existing data IDs/relationships preserved. Import is REPLACE, not merge; independent backup of existing records is essential. Cross-domain storage is origin-specific. Legacy progress photo records (inline data) remain readable, but new progress photos use `photoId`. Data restoration rollback after failure is best-effort, not a guarantee. Never upload real health/photo backups to public GitHub. Code revert does NOT restore deleted browser data.

## Tests
**PASS controlled simulated Chromium:** 17/17 checks, including draft Cancel, commit/remove, export, clean separate browser-context photo import, malformed backup rejection, injected import failure rollback, progress photo persistence and failure, simulated reset, five mobile widths 320/375/390/393/430. Node syntax check passed. **Important:** fake localStorage and fake IndexedDB transactions were used because local HTTP/file navigation was blocked by browser administrator policy. These are not actual storage-persistence E2E passes.
**NOT TESTED / BLOCKED:** iPhone Safari, live Cloudflare preview/build SHA, real IndexedDB on valid origin, refresh persistence, true separate-domain clean restore, storage/quota/permission edge cases, full personal/demo flows, real camera and OS share sheets.

## Release gates
Do NOT merge/deploy beta until: (1) real-origin fresh import of all photo types succeeds; (2) iPhone Safari add/edit/cancel/save/reload pass; (3) quota/perms and rollback handled; (4) full linked-screen regression pass; (5) security defect from audit LUM-BUG-014 (unsafe HTML) and Vault Cleanup defect assessed; (6) explicit user approval. Production remains v0.9.4.

## Known separate defects
Vault Cleanup undefined handler, unsafe HTML rendering, UTC date mismatch, normal modal Escape, demo lower-level write guard, contrast/long lists and other audit backlog remain out of scope.

## Rollback
Previous main SHA 2e02f304dcbb29931d3468dbb51fdbbb2a3bf962. Reverting code is NOT a backup restoration.
