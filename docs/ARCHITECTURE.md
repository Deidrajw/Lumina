# Architecture
Verified 2026-10-24: one static `index.html` with inline CSS/JS, no verified backend, authentication or cloud sync. Records in browser localStorage (`lm_symp`, `lm_conc`, `lm_skin`, `lm_inv`, `lm_steps`, `lm_supps`, `lm_checks`, `lm_photos`, `lm_captures`, `lm_reminders`, `lm_reminder_states`, `lm_activity`, `lm_proto_templates`). Image blobs are saved in IndexedDB and referenced by ID; some legacy base64 image records migrate on startup.

Sections: Today, Body, Protocols, Vault, Insights and Settings. Product entity links routines, symptoms, concerns, photos, insights and doctor summaries. Existing demo uses `readStore()` and `canWrite()` with isolated sample data; test all mutation paths.

Critical gap: `exportData()` embeds `_photoBlobs` but `importData()` does not restore the photo blob store. Do not claim portable backups until tested. Browser storage is specific to protocol/domain/port; Cloudflare hostname changes do not migrate data. Idempotent migrations preserve IDs, links and unknown legacy fields. Keep secrets and actual health data out of public repo; future OCR requires private server-side processing.

## Proposed Phase B v0.9.5-beta.2 architecture (unmerged)
LocalISODate helper aligns daily keys and calendar cells with browser calendar day; no migration of legacy UTC keys. luminaText encodes untrusted values when rendering HTML, preserving raw storage; note only selected views are hardened, and app still uses many dynamic innerHTML and inline handlers. Data access load returns isolated fictional key values in Sample Preview; save rejects preview writes; IndexedDB mutators also reject. No database schema changes. Security/comprehensive mutator audits remain open.
