# Lumina v0.9.5-beta.11 — Backup corruption is not empty data
**Date:** 2026-10-25. **Parent:** Beta10 HEAD 3f568258cc641e8d133d82bba38eac54732b876f. **Branch:** fix/strict-backup-section-reads-beta11. **Production main:** v0.9.4 at 2e02f304dcbb29931d3468dbb51fdbbb2a3bf962 (unchanged).

## Why
Prior general-purpose load(k) catches malformed JSON and returns empty fallback to keep screens usable. This is undesirable for a backup: corrupted saved records could silently be exported as an empty section; post-restore comparison could accidentally treat missing/invalid data as an empty expected section. General screen render behavior should remain tolerant; backup and verification must be strict.

## Source changes / LUM-034
- New pure read-only function luminaReadBackupSection(key,requirePresent=false): looks up known KEYS only; distinguishes absent key vs inaccessible storage vs invalid JSON vs wrong type. New/fresh install missing keys still get correct empty array/checks object defaults for export; requirePresent=true rejects missing destination restored keys.
- exportData reads all 13 keys through the strict reader and blocks export with a visible section-specific message on corrupt JSON, denied access, or unexpected array/object type rather than substituting empty data. No corrupt stored key is changed.
- luminaCheckPhotoBackup blocks and shows an error when the source records are unreadable, never reports a false no-photo result based on corrupted sections.
- luminaVerifyRestoredBackup compares all required imported sections using requirePresent=true, recording missing/corrupt destination keys as mismatches. Already established requirement of all 13 record sections plus N>0 byte-identical photo blobs for overall PASS is unchanged.
- No import, restore rollback, doctor, UI layout, photo IDB write, record schema, or migration changes. Only existing read paths and version/changelog.

## QA
**PASS automated isolated Chromium 90/90**, including 30 negative/functional checks (malformed JSON, null, wrong type, rejected denied storage, corrupt section blocks export, preserves raw string, source photo check blocks, fresh-profile export still valid, missing destination, malformed destination, checks type mismatch, and mocked photo-backed match / mismatch) plus 60 screens: Today/Body/Protocols/Vault/Insights/Settings x 320/375/390/393/430px x dark/light. No page errors or horizontal overflow. PASS Node embedded JS syntax. Fictional data, fake localStorage and mocked photo store only.
**BLOCKED** genuine origin IndexedDB in controlled Chromium due ERR_BLOCKED_BY_ADMINISTRATOR when navigating a routed test HTTPS origin.
**NOT TESTED** actual iPhone Safari, clean-origin photo-backed JSON restore, real quota/recovery, VoiceOver, full linked CRUD/Doctor Summary/security regressions. No production release.

## Data / safety / rollback
No startup migration or automatic storage changes; damaged JSON remains intact for possible recovery. UI export/verification is blocked until bad data is addressed; user may still use existing tolerant screens where practical. No health records/backup images are uploaded to GitHub. Existing restore remains REPLACE after confirmation with best-effort rollback, and is not newly certified. Previous Beta10 source branch 3f568258; production main 2e02f304. Code rollback does not recover lost browser records.

## Next exact step
Verify GitHub and Cloudflare preview SHA. User tests Beta11 fictional cross-origin photo backup on iPhone: save/disposable photos in source origin, export, import into **separate empty** destination origin, refresh and use original backup file with Verify restored backup. Then complete full app QA and security audit before asking distinct approval to merge main.
