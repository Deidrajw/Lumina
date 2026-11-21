# Lumina Master Test Plan — authoritative QA protocol
Updated: 2026-11-21 | Scope: all future Lumina changes | Status: governing protocol (NOT proof of testing)

## Required process for every app update
1. Start by fetching latest main HEAD, working branch HEAD, PROJECT_INSTRUCTIONS.md, PROJECT_STATE, CONTINUITY_LOG, REQUIREMENTS_REGISTER, KNOWN_BUGS, QA_REGRESSION, RELEASE_CHECKLIST and relevant source.
2. Identify requirement IDs (LUM-###), changed functions/surfaces, dependent features, risks, data impact and exact acceptance tests **before editing**. Never silently replace earlier requirements.
3. Work on feature branch; do not alter main or deploy without explicit approval. Preserve approved/LOCKED behaviour. For substantial UI redesign, preview and obtain approval first.
4. Run focused tests plus impacted cross-feature regression; capture actual test evidence, date, commit SHA, build, device/browser/OS, data fixture and tester.
5. Append one dated test run to docs/QA_REGRESSION.md **for every change**, even documentation-only (then state N/A / NOT TESTED for app behavior). Preserve earlier runs. Use the checklist below rather than merely claiming "QA passed".
6. Append one dated handoff to docs/CONTINUITY_LOG.md; update PROJECT_STATE, REQUIREMENTS_REGISTER, KNOWN_BUGS, CHANGELOG and RELEASE_CHECKLIST when applicable. Keep docs with implementation in the same PR.
7. End **every development response** with a compact Continuity Note using docs/CHAT_HANDOFF_TEMPLATE.md. Distinguish work actually done from recommended work, and ask only for user actions that are truly necessary.
8. No release until P0 gates pass and user explicitly approves. Never transform simulated/code-inspection results into manual device PASS.

## Status vocabulary
PASS (automated) = executable assertion passed; record real-vs-mocked components.
PASS (manual) = human executed full workflow on named device/build and observed outcome.
FAIL = reproducible mismatch, with steps/evidence and bug ID.
BLOCKED = could not execute, with concrete blocker.
NOT TESTED = not attempted.
N/A = irrelevant to this change with rationale.
A code review, successful compile or screenshot is NOT an end-to-end PASS.

## Core test environments
- Widths 320, 375, 390, 393, 430 px; light + dark; reduced motion, large text and keyboard/focus where possible.
- Empty, populated fictional data, real-data-preserving personal mode, isolated Sample Preview.
- Real iPhone Safari (iOS version, device and browser recorded); desktop Chromium as complementary, not a replacement.
- At least two **distinct HTTPS origins** for backup portability; new origin must be clean and never an existing personal production address.
- Test loading, success, failure, cancellation, partial/incomplete storage, no results, duplicate, and recovery. Verify after refresh when persistence is relevant.

## Master functional regression catalogue
| ID | Area | Essential acceptance |
|---|---|---|
| M-01 | Navigation/onboarding | Fresh, returning, demo exit; Today, Body, Protocols, Vault, Insights, Settings; correct back and nav state |
| M-02 | Today | Check-in/new and edit, completion indication, reminders, alerts, scroll to final content |
| M-03 | Body symptoms | Create, edit, save, cancel, delete/archive if applicable; photo add/removal, failure, reopen + refresh |
| M-04 | Body concerns | Same lifecycle; photo-backed save and linked product records |
| M-05 | Other photo surfaces | Skin logs, progress photos, Vault/product images, photo lightbox/zoom/exit; camera/file permission denial |
| M-06 | Vault products | Add/search/filter/sort/detail/edit/save/cancel/archive/restore/delete; product links and inventory counts |
| M-07 | Supplement/Rx | Template search results/no results, strengths/forms/timing, active/inactive and doctor summary |
| M-08 | Global search | Search-to-detail-to-edit-to-save/cancel navigation, correct return and updated linked views |
| M-09 | Protocols | Create/read/edit/complete/skip/reorder/calendar/day filtering, weekly and daily views |
| M-10 | Insights | Dates, no-data, observational caveats, linked evidence and summaries; no causal claims |
| M-11 | Doctor tools | Active meds/supplements/sprays time range, selection, report/copy/print/share, safe display of special text |
| M-12 | Imports/exports | CSV paths and JSON complete records; invalid/partial data; confirm replace, cancel, quota and rollback |
| M-13 | Overlays and controls | Every modal/sheet/lightbox closes with X/Cancel/back/outside tap/Escape as applicable; focus/scroll safe |
| M-14 | Settings | Themes, data cleanup preview/cancel/undo, sample mode isolation, clear all including intended IDB |
| M-15 | Data safety | Stable IDs, original data not overwritten, migration idempotence, no cross-mode leaks or private fixtures in repo |
| M-16 | Security and errors | Imported text rendered literally; no unsafe HTML handler; no undefined functions/console errors; failure feedback |
| M-17 | UX/accessibility | Touch targets, type scale, chevrons, colour-independent states, contrast, large text, VoiceOver where available, safe area/scroll |
| M-18 | Performance | Load response, image latency, layout shift, LCP/INP/CLS when measured; never fabricate numbers |

## P0 GATE — real iPhone photo-backed JSON portability (LUM-005/009/033/034)
Precondition: identify exact source and destination version SHA/Cloudflare deployment. Test with fictional records and at least one real, freshly attached image (prefer images in symptom, concern, Vault and progress); preserve source and production data.
1. On source HTTPS origin in iPhone Safari, save fictional photo-backed records. Reload and inspect photos.
2. Export JSON. Keep original file securely in Files. Record section count, linked image count and backup file size without sharing private data.
3. On another clean HTTPS hostname, load compatible beta. Confirm its origin differs and its storage is empty. Never erase production or import into an occupied origin.
4. Import backup; confirm replace; inspect 13 sections, records/IDs, relationships and each photo.
5. Reload destination, close/reopen if appropriate; verify photographs still display and open.
6. Use Settings > Verify restored backup with the SAME JSON, expecting 13/13 sections and N/N linked photo byte/MIME comparisons (N >= 1); document result exactly.
7. Negative checks where safe: incomplete/corrupt source/backup, missing referenced blob, cancelled import, storage quota/error, rollback preserving previous destination records; do not force destructive failures on real records.
PASS only when complete manual Safari evidence demonstrates correct independent-origin restore *after refresh*; verifier output alone does not replace visual inspection. If mismatch: mark FAIL, record exact non-sensitive steps and stop release. Zero-image export cannot pass photo portability.

## Execution layers
A. Per-change focused acceptance suite = new/modified behavior, errors and Cancel.
B. Impacted regression = all readers/writers and linked views affected by shared code or schema.
C. Release full regression = M-01 through M-18, all P0 requirements, physical Safari, origins, performance/accessibility where feasible.
D. Non-app docs change = validate links/paths, requirements, append-only history and test template use; label functional tests N/A or NOT TESTED honestly.

## Evidence and release rules
Each run in docs/QA_REGRESSION.md must contain: date/timezone, test ID, LUM ID, app version, exact commit SHA, preview URL/build identity, environment, tester, setup/fixture, steps/expected, result, evidence pointer (screenshots/log excerpt sanitized or 'none'), notes/bugs and re-test status.
Personal backups, photos, wellness data, secrets, raw photo blobs, browser storage and screenshots containing personal data must never be committed to this public repository.
Blocked/P0 FAIL/NOT TESTED ⇒ release NO-GO. Record rollback code SHA and remind that code rollback does not recover browser data.
