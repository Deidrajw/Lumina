# Lumina Beta11 — Backup Corruption Guard (2026-11-20)
Version 0.9.5-beta.11, build 2026.11.20.backup-integrity.1. Branch fix/backup-corruption-guard-beta11, parent Beta10 commit 3f568258cc641e8d133d82bba38eac54732b876f; production main 2e02f304 unchanged.

## Finding and change
The shared load() function swallows malformed JSON and returns a default empty section. Beta10 exportData and luminaVerifyRestoredBackup used it, risking an apparently complete export with omitted records and false restore matches if both source and destination were malformed. Introduced luminaReadBackupSection(key,fallback), a strict **backup-only** reader. If the key is absent (fresh install), returns [] or {}. If present, JSON must parse and match the section type: checks a non-null non-array object, other 12 sections arrays. Otherwise throw without exposing stored content. exportData catches and blocks download, verifier catches and reports NOT VERIFIED. Ordinary app screens keep existing forgiving load() and no stored data changes.

## Requirements
LUM-034 P0, BUG-035. Preserve schema, record IDs, IndexedDB photos, backup v2 and legacy compatibility. No automatic migration, mutation, reset or data exposure. No user records in GitHub.

## Tests
PASS Node synthetic 15/15 and embedded JS syntax. Tests: valid and missing sections, truncated JSON, wrong types, null, scalars, strict reader use in both export and verify, ordinary load unaffected. NOT TESTED actual browser UI (Chromium executable unavailable), real iPhone Safari, actual IndexedDB clean-origin export/import/refresh, real quota/rollback, full app regression/VoiceOver. Tests do not certify portable photo backup.

## Tester acceptance
On Cloudflare Beta11 preview with disposable fictional data: save sample symptom and photo, export JSON, verify the downloaded file. On another distinct origin import and refresh, verify 13/13 and N/N image bytes. Do NOT intentionally corrupt real production records. Developer-only malformed JSON tests must use an isolated disposable origin and be reset afterward. If backup says incomplete, do not move origins or delete old data.

## Data, rollback and next step
No schema migration. Existing malformed data remains untouched and cannot be exported until repaired or recovered; do not reset automatically. Restore still best effort on quota failure. Rollback to Beta10 code commit 3f56825, which does not restore lost records. Next: real Safari clean-origin photo restore, quota and full regression, then separate explicit production merge approval.