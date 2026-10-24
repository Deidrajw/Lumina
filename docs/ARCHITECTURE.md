# Architecture
Verified 2026-10-24: one static `index.html` with inline CSS/JS, no verified backend, authentication or cloud sync. Records in browser localStorage (`lm_symp`, `lm_conc`, `lm_skin`, `lm_inv`, `lm_steps`, `lm_supps`, `lm_checks`, `lm_photos`, `lm_captures`, `lm_reminders`, `lm_reminder_states`, `lm_activity`, `lm_proto_templates`). Image blobs are saved in IndexedDB and referenced by ID; some legacy base64 image records migrate on startup.

Sections: Today, Body, Protocols, Vault, Insights and Settings. Product entity links routines, symptoms, concerns, photos, insights and doctor summaries. Existing demo uses `readStore()` and `canWrite()` with isolated sample data; test all mutation paths.

Critical gap: `exportData()` embeds `_photoBlobs` but `importData()` does not restore the photo blob store. Do not claim portable backups until tested. Browser storage is specific to protocol/domain/port; Cloudflare hostname changes do not migrate data. Idempotent migrations preserve IDs, links and unknown legacy fields. Keep secrets and actual health data out of public repo; future OCR requires private server-side processing.

## Proposed Phase B v0.9.5-beta.2 architecture (unmerged)
LocalISODate helper aligns daily keys and calendar cells with browser calendar day; no migration of legacy UTC keys. luminaText encodes untrusted values when rendering HTML, preserving raw storage; note only selected views are hardened, and app still uses many dynamic innerHTML and inline handlers. Data access load returns isolated fictional key values in Sample Preview; save rejects preview writes; IndexedDB mutators also reject. No database schema changes. Security/comprehensive mutator audits remain open.


### Beta.3 technical note (unmerged)
Escape now prioritizes confirmation, lightbox, open modal/sheet, then underlying product detail. Uses existing closeModal cleanup; no new store fields or migrations. Smart Capture remains manual without OCR integration. Printed summary and recent capture cards use display-only luminaText escaping; data at rest remains raw/editable. Preview avoids persisting theme/onboarding/profile/version/dev flags. Other dynamic HTML sinks and direct writers need review.


## Phase D beta.4 unmerged improvements
Existing record schema/localStorage KEYS and photo blob database unchanged. Vault JSON importer now delegates to the same validated Settings importData and luminaRestoreBackup pipeline; no unconfirmed direct JSON restores. CSV remains a separate, user-selected replace/merge flow and now checks saves. Dynamic global search renderer is built using DOM textContent/event listeners instead of interpolating imported text/action strings into innerHTML, but a search-results host is not currently mounted in the UI. Product page text rows, journal, linked conditions and picker rendered with luminaText; gallery uses DOM src/event listeners. CSV mapping/preview escapes imported values; Rx custom effect chips use textContent. Stored values stay raw/editable. Broader security review and genuine origin photo restore remain pending.


### Beta8 backup and Doctor Summary hardening (unmerged)
Doctor Summary confirmed selection HTML now escapes all raw item text at output boundary; item selection inputs bind via numeric indices and event listeners, avoiding untrusted IDs in inline handler strings; generated summary and presentation render also escape fields. No stored data changed. Settings photo check reads only IDB refs from the same existing backup ref collector, counts Blob MIME/size and missing refs without mutations. Version2 JSON requires all KEYS fields (13 data sections), normalizes empty missing checks to {}; old legacy partial JSON still valid. Restore decodes and validates image blobs before saving; uses existing attempted rollback. On-device photo check **does not** promise portable backup or test clean-origin IDB. Schema/backends unchanged.
