# LUMINA — COMPLETE UI/UX HEURISTIC REVIEW & IMPLEMENTATION PLAN

**Audit date:** 2026-10-24 · **Version audited:** v0.9.5-beta.4, GitHub branch `fix/lumina-import-display-safety-v0.9.5-beta.4`, commit `d33e0cec1ba635e201772a5093dbb84e4a348282`, root `index.html` blob `67184b00b45959446f1403d75e6f20d24ad2611f`. **Production:** `main` at `2e02f304dcbb29931d3468dbb51fdbbb2a3bf962`, v0.9.4.

**Basis:** Direct code review of current beta, existing isolated app screenshots, fresh synthetic browser checks, the 81-page uploaded *UI/UX Design — Practical Study Guide* (October 23, 2026), and prior documented Lumina audit/QA history. All sample entries are fictional. This is an expert heuristic audit and targeted isolated testing, **not** a real-user usability study, accessibility certification, device performance benchmark, or completed photo-backup acceptance test. User has confirmed the earlier Cloudflare preview opens in Safari; specific photo/save/restore tests are still pending.

## Executive assessment

**Direction: preserve the brand; change the hierarchy, not the identity.** Lumina's Instrument Serif, Manrope, plum, mauve, warm metallic accents, card styling, and product-centered relationships provide a recognizable premium identity. Several UX weaknesses come from competition among similar cards, small/low-contrast secondary text, options hidden behind overflow, inconsistent action signifiers, and uncertainty about save/restore. Do not “solve” them by introducing more tabs, more carousels, or hiding important warnings.

**Trust hierarchy:** preserve records/photos and recover from failures → clarify the highest-value task and saved status → group secondary information → unify component semantics → make layouts legible and tappable → measure real usage and performance.

### What was actually checked
- GitHub `main` and Beta 4 HEAD, project state, changelog, requirement register, known bugs, QA log and design system; beta4 HTML blob matches checked-in local working file.
- Static HTML contains **6 main panels** (Today, Body, Protocols, Vault, Insights, Settings), **5 primary nav buttons** plus Settings header entry, **39 static backdrop containers**, **268 inline `onclick` attributes** and 234 static button elements. These counts indicate maintenance/a11y audit scope, **not 39 demonstrated broken overlays**.
- Baseline CSS: `--tx3` dark `#635d72` has ~**2.75:1** contrast against main card `#1c1925`; light `#9b93ac` ~**2.93:1** against white; bottom nav labels **9.5px**, Settings icon button **36px**, form inputs **14px**, viewport `maximum-scale=1`.
- Current Beta 4 known-functionality notes: photo-aware Settings import and updated Vault JSON path, targeted output escaping, manual capture copy, overlay Escape and demo guards are implemented candidates. These **have not** received comprehensive real-device QA.
- Updated Beta 5 isolated Chromium render checks: **60/60 PASS**, all six tabs × five widths (320,375,390,393,430) × two themes, with simulated localStorage and fictional samples; no horizontal page overflow and no uncaught page errors. Additional concept studio six-tab navigation/search/theme tests PASS. This does not certify iPhone Safari, touch/keyboard/VoiceOver, or real IndexedDB.

## Principles applied from the user-supplied guide

| Guide section/page | Principle | Lumina application |
|---|---|---|
| pp. 1–3, 8–9 | Goal first; visual hierarchy is what users notice first; IA is where features belong | Today should emphasize next check-in, saved status and relevant alerts, not make all information visually equal. |
| pp. 11–20 | Tabs represent related peers; selected state + descriptive labels; don't hide critical status | Body and Protocols need recognizable destinations, stable selected state and visible overflow. |
| pp. 21–23 | Sheets versus modals versus full pages | Simple filter/product selection suits sheets; complete product setup may require grouped, sustained form flow. |
| pp. 30–33 | Timeline ≠ chart; bounded progress ring; drag needs non-drag alternative | Explicit date/context; percentages need real denominators; reorder needs Move Up/Down. |
| pp. 35–39 | Typographic scale, whitespace, proximity, common region | Group related entries, use predictable gutters and readable metadata; reduce nested cards. |
| pp. 40–50 | Before/during/after feedback; cognitive load; recognition; empty states; recovery | Confirm persisted Save; preserve Cancel drafts; show one observation with evidence, then details. |
| pp. 51–55 | Heuristics, Hick/Fitts, responsiveness/accessibility | Larger targets, text zoom, focus states, short action lists. |
| pp. 59–65 | Measured LCP/INP/CLS, design-token consistency and accurate microcopy | Do not claim speed results without measuring; no fake OCR or cloud sync claims; align icons/statuses. |
| pp. 66–79 | Real task, success criteria and usability observation | Test first-time add/photo/save, find product/edit, review insight, export+restore and complete reset. |

## Screen-by-screen UX audit

### A. Today — **P1: visual hierarchy / dense alerts / trust in progress**
**Goal:** know what matters today, finish a check-in, and identify urgent follow-up.
**Verified observations:** Headline, date, three progress rings and four same-weight metric tiles precede concerns, today symptoms, an optional skin check-in, reminders and observation. In the preloaded fictional demo, a large count of expired/reminder cards extends the screen. The three rings show equal 0–100 completion treatment; individual denominators aren't visually explained, and 0% can ambiguously mean none scheduled or incomplete. Reminders auto-expand if urgent and show a long list. The existing list does have a “more” affordance; don't remove actionable alerts.
**Principles:** clear focal point, Hick's law, feedback, bounded progress, progressive disclosure.
**Proposal for approval (NOT implemented in app):** one dominant Today status/Log CTA, compact bounded routine progress (“2 of 3 scheduled”), 2–3 supporting metrics, “Needs attention” summary with visible count plus a disclosure for all items, and one observation with linked evidence. Keep urgent presence visible even when details collapse; do not hide truly critical information.
**Acceptance:** first-time visitor can locate next check-in in five seconds, see precisely how many scheduled steps are done, open every reminder, and find prior logging; all counts unchanged from existing data.

### B. Body — **P1: task-first entry, consistent filters and history**
**Goal:** log/edit symptom or concern including picture, view related records and history.
**Verified observations:** Symptoms, Concerns and overflow Skin Log / Rx Check-ins / Progress use a compact tabs-plus-more scheme. Symptom severity and category filters add visual controls before history. Modal forms are long and photo edits have previously had data risks, addressed in unverified Phase A candidate. Some card labels and metadata are too small.
**Principles:** information scent, recognition vs recall, progressive disclosure, reliable Cancel/Save, accessible combobox.
**Proposal (NOT implemented):** expose quick +Log and distinguish Symptoms/Concerns/other logs more clearly, consolidate optional filters in a labelled filter sheet, make linked product/photo controls optional after essential fields, and keep a persistent Saved/Failed response. Test camera permission, cancel photo removal, and lost network/browser quota.
**Acceptance:** create→attach→save→refresh→edit→cancel/commit across all photo types; no orphaned image; failure preserves draft. Search/filter count and edit navigation remain stable.

### C. Protocols — **P1: related tabs, choice density, reorder affordance**
**Goal:** see today's actual routines, mark steps completed, select supplement/prescription and edit schedules.
**Verified observations:** Six modes share the Protocols parent: AM, PM, Supplements and overflow Hair/Rx/Week. Routines use compact stacked rows; some metadata 10–12px; many tap targets could use larger spacing. A drag indicator exists in historic code but true touch reorder not confirmed by current device test.
**Principles:** tab peer groups, Fitts's law, signifier consistency; guide p.33 says don't make drag the only method.
**Proposal (NOT implemented):** keep AM/PM and Supplements clear; group secondary modes under descriptive “Other routines” rather than vague More when practical; show completion with exact denominator; add Move Up/Down fallback and Save confirmation after rearrangement.
**Acceptance:** scheduled day selection correct on DST/date changes; add/reorder/complete and refresh; overflow is easy to discover and no accidental touch scroll conflicts.

### D. Vault — **P1: findability, density, product hub integrity**
**Goal:** find a specific product quickly, know active/in-use/expired stock and edit safely.
**Verified observations:** Long stacked list of in-use items with brand, type, percentage, expiry/status badges; multiple small, similar text treatments per row. Vault has search, filter sheet, review/cleanup and import/capture. Past reported Cleanup error is fixed in beta, not independently device-verified. An internal global-search renderer exists but has no mounted UI host currently; do not claim functional global search across screens.
**Principles:** hierarchy, grouping, recognition, concise metadata, context menu for secondary item actions.
**Proposal (NOT implemented):** place searchable In Use list near top with stronger product-name row, one clear status, secondary details in product page; “Needs review” summary not repeated per row, Archived/Empty collapsible; grouped product form (“Basics,” “Inventory,” “Linked routines,” “Notes/photos”).
**Acceptance:** 20+ items manageable at 320px and with Dynamic Type; filters persist through edit/return; search to edit remains contextually consistent; linked records retain IDs.

### E. Insights — **P1: interpretation versus evidence**
**Goal:** understand what was recorded, over what period, and whether an observation warrants a closer look.
**Verified observations:** Top category observation, changed recently list, symptoms by category, severity split, patterns shortcut, skin patterns, medication observations and things-to-watch are stacked. Multiple periods appear (selected range versus “3 days” section), so the timeframe should be explicitly shown for every observation. No output should imply products caused symptoms. “Low/Medium/High confidence” wording needs evidence definitions or careful language.
**Principles:** one takeaway before evidence, data provenance, avoid colour-only meaning, lower cognitive load.
**Proposal (NOT implemented):** first show a single plain-language observation + timeframe + sample size + caveat; expandable “supporting entries,” then trends; put historical/secondary analyses into named groups. Avoid numerical severity/progress visualizations without meaningful denominators. No inference of treatment effectiveness from a few anecdotal notes.
**Acceptance:** each insight has timeframe, record count, clickable evidence, no causation claim and appropriate missing-data state; older and zero values differentiated.

### F. Settings, professional summaries, imports, onboarding and demo — **P0 trust, P1 IA/microcopy**
**Goal:** adjust preferences, export a clear professional summary, and reliably back up/restore personal data.
**Verified observations:** Settings contains many data, reports, preferences and developer controls. Export/Import are distinct from Vault's import workflow (the JSON paths were unified in beta4). Cross-origin browser storage is not portable without a full photo restore. Dangerous Delete/Clear actions need prominent explicit scope and recovery guidance. Demo Preview must be fictional and fully isolated, including settings and photo writes. Developer controls are not appropriate for ordinary users once released.
**Principles:** user control, error prevention, trust signals, descriptive microcopy, progressive disclosure.
**Proposal (NOT implemented):** Keep Backup/Restore and Doctor Summary highly discoverable; group Preferences separately; hide developer tooling in development builds rather than ordinary production; display honest local-only data status and last successful export (if implemented and persisted). Introduce restore review page with record/photos counts, replacement explanation and success validation.
**Acceptance:** new browser origin restores all linked records and IDB photos from synthetic backup, refresh persists, partial/corrupt backup rejects without mutating previous records, Clear deletes both stores as claimed.

### G. System-wide components — **P1 universal accessibility / polish**
**Measured baseline:** small labels, low-contrast `--tx3`, fixed viewport zoom, 36px icon controls, many manually generated HTML strings and inline handlers; focus and accessibility names inconsistent. The single-file source raises regression risk as UX tweaks touch many common patterns. There are 39 overlay/backdrop elements, **not a proof that all are dysfunctional**. Several outputs have been escaped in beta2–4 but broad XSS/data mutator audit is incomplete.
**Implemented as v0.9.5-beta.5 candidate (smallest possible surface):** `--tx3` contrast improvements, readable nav headings, 44px Settings icon and 44px tab targets, focus-visible outline, reduced-motion support, form input type size 16px for Safari, browser zoom restored, active navigation `aria-current="page"` and named navigation/settings affordances. No record migration, no change to UI information architecture or card/data schema.
**Measured contrast change:** dark tertiary against main card ~2.75:1 → ~5.37:1; light tertiary on white ~2.93:1 → ~5.82:1. Confirmed via calculation on flat token pairs, not a full WCAG audit of every overlay, opacity and gradient.
**Device verification still required:** VoiceOver and keyboard/tab cycling, 200% zoom, safe-area and home indicator, dynamic text, long imported content, 320px forms, OS photo picker, real Safari, reduced-motion behaviour and contrast over alpha/translucent surfaces.

## Proposed priority register

| Requirement | Priority | Kind | User-visible outcome | Status |
|---|---|---|---|---|
| LUM-021 — accessibility foundation | P1 | Nonstructural update | Contrast, mobile tap/focus/zoom and nav labels | **Implemented beta.5; isolated tests PASS, Safari not tested** |
| LUM-022 — Today hierarchy | P1 | Substantial redesign | Clear primary check-in, compact progress, grouped reminders | **Proposed only; design approval needed** |
| LUM-023 — Vault inventory clarity | P1 | Substantial redesign | Search and status scannable; secondary details collapsed | **Proposed only; approval needed** |
| LUM-024 — Insights evidence-first | P1 | Substantial redesign | One observation first, evidence/timeframe on demand | **Proposed only; approval needed** |
| LUM-025 — Body and Protocols navigation/forms | P1 | Substantial redesign | Quick task, filters in sheet, reorder alternatives | **Proposed only; approval needed** |
| LUM-026 — Save/error consistency | P1 | Function / QA | Consistent persisted/save failed/draft preserved and honest local-only status | **Requested; full workflow audit pending** |
| LUM-027 — screen-reader and performance baseline | P2 | QA | VoiceOver and Core Web Vitals measured on production/preview | **Not tested** |
| LUM-008–020 older work | P0/P1 | Existing beta candidates | Photo lifecycle, restore, security, Demo Preview isolation | **Implemented candidates, not end-to-end verified** |

## Suggested sequence
1. **Now:** review Beta 5 accessibility improvements in Cloudflare branch preview; test at 320/390 with large Safari text and focus (if external keyboard). Compare dark/light.
2. **Before any production release:** confirm synthetic cross-origin photo export+restore, complex Cancel/Save, demos, browser quota and import rollback; run security scan beyond the subset hardened in beta.
3. **Next design approval:** review the separate interactive six-screen UI/UX Concept Studio. Pick/adjust proposed layouts for Today, Vault and Insights first. Only after approval adapt current renderers, preserving functions and links.
4. **After redesign implementation:** full app regression, accessibility checks, state persistence, Cloudflare branch preview and production approval.

## Actual QA outcome for beta.5 (not beta4 E2E)
- **PASS automated isolated Chromium (60/60):** six main panels × five widths × dark/light, no document horizontal overflow or page exceptions; `aria-current` navigation matches each active main tab; Settings has no misleading selected bottom-nav destination; nav label computed >=11px and Settings button 44px.
- **PASS static:** embedded script `node --check`; app source loads with fictional Sample Preview; current v0.9.5-beta.5 announcement/changelog entry adds without overwriting beta4 historical release notes.
- **PASS concept studio:** six nav views render without overflow at 390px; fictional Vault search filters mock records; theme toggle works; no page errors.
- **NOT TESTED:** end-to-end personal/demo CRUD, photo persistence and restore, full phone OS keyboard/VoiceOver/Safari, entire injection audit, `LCP/INP/CLS` metrics; prior screenshot/QA is not proof of real iPhone outcome.
- **DEPLOYMENT:** Branch PR preview may be generated by Cloudflare after GitHub push; don't call it deployed until check confirms. Production `main` must remain v0.9.4 without explicit approval.

## Artifacts / recovery
- `index.html`: actual nonstructural v0.9.5-beta.5 candidate (same `KEYS` schema and all existing app features).
- `Lumina_UIUX_Concept_Studio.html`: separate fictional interactive proposed layout; **not** app code, no writes.
- `UIUX_Accessibility_Before_After.png` and six actual beta screenshots: browser-rendered visual evidence.
- Full ZIP: root `index.html`, preview, audit, release notes, QA checklist, concept assets.
- Rollback source baseline: latest production `main` SHA `2e02f304` and previous beta4 SHA `d33e0ce`; code rollback does NOT recover lost browser data. No user records were imported, written or committed for this audit.
