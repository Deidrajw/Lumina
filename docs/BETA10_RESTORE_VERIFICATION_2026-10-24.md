# Lumina Beta 10 — Real-backup restore verification tool
**Date:** October 24, 2026 | **Version:** v0.9.5-beta.10 | **Build:** 2026.10.24.restore-verify.1
**Feature branch:** fix/restore-verification-beta10, parent Beta9 3a2c88edc7762622ce432415325c6ecee302fe2b.
**Production main:** 2e02f304dcbb29931d3468dbb51fdbbb2a3bf962, v0.9.4, unchanged.

## User intent & scope
The user asked to continue after Beta9. The highest open release gate is genuine photo-backed JSON export → import → refresh on two distinct HTTPS browser origins. Previous isolated Chromium mock tests don't verify IndexedDB or Safari. This beta adds a **local, read-only post-import comparison** so Safari can report objective evidence without sharing private backups, using Lumina's actual storage and photo APIs. Approval covers test branch and Cloudflare preview only, NOT production merge.

## Features (LUM-033, prerequisite for LUM-005/009)
Settings > Backup & Restore adds **Verify restored backup** with explanatory text and a local JSON file input. On the destination HTTPS origin, user selects original JSON after an ordinary, explicitly confirmed import. Implementation validates the file with existing luminaValidateBackup, requires all known 13 stored sections for an overall PASS, compares each to current browser localStorage as canonical JSON (sort object keys, preserve arrays), and compares every referenced IndexedDB photo Blob's MIME type, byte length, and full byte sequence to decoded payload in the original file. No uploaded data or external service. Read-only: no call to save, localStorage.setItem, luminaSavePhoto, Delete, or importData. Only a textual status is written to the page.

A result of **PASS** requires *all 13 sections match and N/N linked images match with N>=1*. Missing or differing photos and records, incomplete legacy file, malformed backup, and zero-photo input yield **NOT VERIFIED** with a summary. This does NOT promise unrelated features like camera/VoiceOver work, and a pass in Chromium does not replace the required user-run iPhone Safari test.

## Test evidence
- PASS Node embedded JS syntax.
- PASS 77/77 **isolated Chromium** synthetic tests: 13 sections/4 fictional linked photos match; intentional one-byte mismatch, missing image, changed record, malformed backup, partial legacy, zero-photo and Sample Preview cases detect correctly; selected JSON via real FileReader reports pass while 13 stored record keys unchanged; 60 view-width/theme combinations (320, 375, 390, 393, 430; dark/light; six tabs) no page exception/horizontal overflow.
- BLOCKED genuine local HTTP and dummy HTTPS Chromium navigation: ERR_BLOCKED_BY_ADMINISTRATOR. Tests mocked current-origin storage and photo read function; **no real browser IndexedDB persistence/restore was performed.**
- NOT TESTED iPhone Safari actual cross-origin restore, quota/error recovery, full app/Doctor Summary/VoiceOver/security checks. Previously reported Beta9 checks not independently rerun.

## Data/migration, regression risk, rollback
No new storage keys, IDs, database schema, data migrations, writes, backend, OCR or sync. It compares only current records; serialized photo payload stays within user-selected JSON and browser memory while processing. This is no certified recovery until separate origin import works in Safari. Large photo files may temporarily increase memory when decoded and compared. Beta9 source fallback 3a2c88e; production main 2e02f304. Rolling back code cannot recover lost browser records.

## Test on iPhone Safari with fictional data
1. Open source immutable Beta10 Cloudflare preview, check Settings version, create fictional Symptom/Concern/Vault Product/Progress entries each with disposable image.
2. Save, refresh, visually reopen all four photos. Settings > Check saved photos; verify four readable IDB links.
3. Settings > Export JSON; retain the **original file** on device (do NOT send private copies).
4. Open Beta10 Cloudflare branch alias (different hostname). Confirm this destination contains **no valuable data**, then Import JSON, review **REPLACE** warning, accept. Refresh and reopen photos.
5. Settings > Verify restored backup, select the **same original JSON file**. Expected PASS indicates 13/13 matching sections and 4/4 (or other N>0) byte-identical linked photos. If failure, do not treat backup as portable; report counts and affected category names, never personal names/photos.
6. Independently test Cancel, quota/permission, dark/light and VoiceOver; do not merge/release until documented.

## Next exact step
Verify GitHub branch/PR and Cloudflare preview SHA. User carries out real iPhone Safari acceptance and reports count/status. Then audit remaining direct HTML sinks and storage rollback/failure cases, complete full regression, and obtain **separate explicit approval** for any production merge/deploy.