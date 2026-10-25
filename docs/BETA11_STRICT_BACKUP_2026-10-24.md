# Lumina v0.9.5-beta.11 — Strict Backup Read Integrity
Date: October 24, 2026. Feature branch fix/strict-backup-integrity-beta11. Base Beta10 HEAD 3f568258cc641e8d133d82bba38eac54732b876f. Production main v0.9.4 at 2e02f304dcbb29931d3468dbb51fdbbb2a3bf962 unchanged.

## Why this patch
Code review identified a false-backup-integrity risk: general load() intentionally catches JSON parse failures and substitutes an empty default. Export, Check saved photos and restored-backup verification used it, potentially treating corrupted saved records as valid empty data. The project already has a true physical Safari photo-backup release gate; the verifier must not certify corrupted/missing sections.

## Source changes
- Introduced luminaReadBackupSection: a read-only strict reader for the existing localStorage KEYS. An absent first-run optional key yields a correct empty list/checks object; a malformed or wrongly typed present section throws. When verifying a restored backup, missing destination keys are treated as mismatches.
- exportData: builds its JSON through strict reads and explicitly blocks exports with a stored-data error, never replacing corrupt data with empty arrays.
- luminaCheckPhotoBackup: refuses reassuring photo readiness when source record sections are corrupt.
- luminaVerifyRestoredBackup: marks each missing, unreadable or type-invalid section as differing from the original JSON. Existing photo byte-for-byte verification is otherwise unchanged.
- Version v0.9.5-beta.11 / build 2026.10.24.strict-backup-read.1 and in-app changelog. All previous features included.

## Data/migration/privacy
No new localStorage key, record field, IDB photo migration or stored-data mutation on startup. Corrupt records are not automatically repaired or discarded. More conservative backup warnings may prevent download until underlying data issue is handled. All synthetic QA records fictional; never share personal JSON, photographs or tokens in public GitHub.

## QA
PASS Node --check full embedded source. PASS 16 of 16 focused isolated Chromium checks against exact functions extracted from root index.html with mocked localStorage (empty vs missing, corrupt JSON/type, export fails safely, preflight blocked, verifier detects missing/corrupt, no-photo cannot falsely pass). Full app set_content was attempted but timed out, NOT counted. Real browser origin navigation for localhost/file/dummy HTTPS returns ERR_BLOCKED_BY_ADMINISTRATOR, so real IndexedDB cross-origin restore cannot be tested here. Physical iPhone Safari, camera/photo persistence, full mobile/light/dark and VoiceOver regression NOT TESTED. Previously recorded Beta10 test outcomes are historic only.

## Status and risk
IMPLEMENTED review beta. NOT VERIFIED for Safari or full end-to-end backup. Production NO-GO. Prior best-effort rollback and legacy partial backups unchanged, and they remain risk. Beta10 code rollback SHA 3f568258; production main 2e02f304. Reverting code cannot restore damaged browser data.

## Next exact step
Verify Cloudflare branch build SHA, user tests disposable fictional source photo export -> different Cloudflare hostname import -> refresh -> Verify restored backup (13/13 sections, N/N images with N>0), and report status without sharing the actual JSON. Follow with full regression and explicit merge approval.
