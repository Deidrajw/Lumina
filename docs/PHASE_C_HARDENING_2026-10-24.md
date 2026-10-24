# Lumina — Phase C release hardening (v0.9.5-beta.3)
**2026-10-24 | NOT DEPLOYED | DO NOT MERGE TO MAIN UNTIL VERIFIED**
Base: PR #3 Phase B commit c6ac809; production main 2e02f304/v0.9.4. Feature branch: fix/lumina-release-hardening-v0.9.5-beta.3.

## Requirements / changes
LUM-016 / BUG-017: Escape closes modal/confirmation using existing cancel cleanup before closing underlying product page; photo and symptom forms included. Focus restoration, dirty-form confirmation and some non-backdrop overlays remain to review.
LUM-017 / BUG-016: Smart Capture landing no longer claims connected AI/OCR; manual photo and product details are accurate. Recent capture history escaped.
LUM-013 / BUG-014: Printable Doctor Summary escapes user-entered HTML from symptoms, concerns, prescriptions and supplements. Handles popup blocked case. Other renderer and inline HTML handlers remain unverified.
LUM-015 / BUG-019: Sample Preview now avoids persisting theme, onboarding profile/goals/completion, update-seen and developer mode flags; existing central save/photo guards retained.
App version/build updated to 0.9.5-beta.3 / 2026.10.24.phase-c.1. No other layout redesign or data changes.

## QA
PASS Node JavaScript syntax and 16/16 focused automated isolated Chromium cases with fictional data/in-memory localStorage; includes Escape normal/modal/confirm/product/photo, Smart Capture copy, malicious print and capture records, sample preference guards and five viewport widths (320,375,390,393,430px). No uncaught page errors in this run.
BLOCKED: local HTTP navigator returned ERR_BLOCKED_BY_ADMINISTRATOR; could NOT certify actual IndexedDB, cross-origin photo export/import, or Cloudflare SHA.
NOT TESTED: real iPhone Safari, camera, mobile keyboard, PDF print OS UI, full audit of HTML injection sinks and direct storage writers, all modal focus/unsaved flows, full doctor exports, comprehensive E2E. Previously recorded simulated Phase A 17/17 and Phase B 13/13 not rerun in this turn. Never label these Verified.

## Data protection / recovery
Code does not intentionally migrate or delete existing records and uses legacy field structures. Browser localStorage and IndexedDB remain origin-specific; the new Cloudflare URL cannot read records from an old host automatically. Beta preview is fictional and read-only. Code rollback to main SHA 2e02f304 does not recover lost user records. Don't import actual private data into an unverified beta.

## Next steps
Review PR #1 -> PR #2 -> PR #3 -> this beta draft PR in order. Complete real-origin Safari backup/restore, broad XSS/data isolation audit and cross-feature QA before requesting production merge. Then propose Today and Insights visual hierarchy refinement for user approval.
