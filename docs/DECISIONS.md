# Decision Log (append and supersede, never silently rewrite)
- **DEC-001 (2026-10-24):** Executable truth is latest GitHub main/root index.html, not old Claude notes; current version v0.9.4.
- **DEC-002:** Preserve present Instrument Serif/Manrope and mauve/plum luxury theme; major redesign needs approval.
- **DEC-003:** Store requirements, bugs, QA, continuity, changelog, architecture, release state in GitHub.
- **DEC-004:** Use docs/feature branches and PR previews; do not change production until approved.
- **DEC-005:** Cloudflare Pages with Git integration is intended, not yet verified connected; main intended as production.
- **DEC-006:** User data local-first, no actual backups/PHI in public GitHub; domain migration requires verified photo-preserving export/restore.
- **DEC-007:** Lumina is personal tracking, not medical diagnosis; observational insights; no fake OCR or notifications.

- DEC-011 (2026-10-24, beta proposal): Protect stored user strings at display/output boundaries rather than altering saved text; preserving search, edit and export. Existing inline HTML composition needs broader hardening and future refactor.
- DEC-012 (2026-10-24, beta proposal): New daily/calendar calculations use browser-local date keys without rewriting existing historical UTC-derived data. Migration deferred until tested and approved.
- DEC-013 (2026-10-24, beta proposal): Enforce Sample Preview read-only boundary in central save and image persistence primitives, not only individual forms.


- DEC-014 (2026-10-24, proposed on beta.4): Vault and Settings JSON backups use a single validated REPLACE flow with photo completeness and user confirmation; remove competing legacy import shortcut. CSV imports retain explicit merge/replace choice.
- DEC-015: Where practical, use DOM textContent and event listeners instead of constructing user data inside innerHTML and onclick. Escape displayed values; do not alter persisted raw strings. Review all remaining HTML sinks in future work.
- DEC-016: Keep beta previews on feature branches and use fictional isolated sample data; user's ability to open beta.3 in Safari is a preview deployment confirmation, not a photo restore test.


- DEC-017 (2026-10-24, beta proposal): Preserve Lumina's Instrument Serif/Manrope, plum/mauve visual identity; solve information density through hierarchy and progressive disclosure, not a new brand design.
- DEC-018 (candidate implemented): Improve text contrast, visible focus, touch sizes and semantic current-page selection without changing data schema, functional layout or existing primary navigation.
- DEC-019 (proposal, awaiting user approval): Group Today alert detail, Vault product status, and Insights supporting metrics/evidence. Never hide critical status or claim observed association caused a symptom.
- DEC-020: Match UX proposals to the supplied 81-page UI/UX study guide; measure real task success and performance instead of equating aesthetic appearance with functional verification.


- DEC-021 (2026-10-24): User says “i approve” of six-screen UI/UX concept. Approves planned layout implementations on feature branches, not merge/deploy to production.
- DEC-022: Batch 1 covers Today/Vault/Insights first for small regression surface. Body, Protocols, Settings designs remain approved for separate reviewable implementation.
- DEC-023: Today total uses real scheduled routine step count + one daily skin check-in; dash when none scheduled rather than misleading zero. Not a health/adherence rating.
- DEC-024: Use native details/summary and semantic buttons for discoverable optional content, preserve all existing lists/edit routes, and maintain observational context on Insights.


- DEC-025 (2026-10-24): User-approved six-screen design implemented in two incremental batches, Beta6 and Beta7, without merging to main or altering record structures.
- DEC-026: Surface existing Show all and Reorder protocol affordances with truthful counts, disable unsupported supplement controls.
- DEC-027: Separate professional summaries from backups and hide destructive reset behind discoverable native disclosure. Existing functionality remains available.


- DEC-028 (2026-10-24): Treat UX heuristic scores and release-readiness evidence as **separate** dimensions. Every significant Beta7 page/subflow gets reviewer strength, gap, severity and acceptance; no self-graded numeric score implies Verified functional testing.
- DEC-029: Data safety and unescaped Doctor Summary output are production release gates even when visual grade is good; feature branch patches/real-origin regression precede merge.
