# Lumina — Every-page UI/UX and delivery scorecard
2026-10-24 | Graded source: Beta7 at b48dca80645540ab45d483e5283af947b44aaa6d | Production main v0.9.4 at 2e02f304 unchanged.
**Scope:** 57 individually graded navigation, subview, editor, and action-sheet surfaces. This is an AUDIT ONLY, no application code changes.

## Source and methodology
User's 81-page UI/UX Design Practical Study Guide: six-question preflight pp.2–3; usability heuristics, Fitts/Hick pp.50–53; mobile accessibility pp.54–55; performance pp.60–61; project discovery/validation pp.67–71; screen checklists pp.78–79. Each UX /100 uses task clarity 20, navigation/discoverability 20, feedback/error recovery 20, mobile/accessibility 15, content/consistency 15, data trust 10. A=90+, B=80–89, C=70–79, D=60–69, F<60. Scores are provisional **reviewer judgments**, not measured task success or WCAG certification.

## Product overview
**Unweighted average: 73/100 (C).** Today 85; Body views 75.4; Protocols views 75.7; Vault views 73.2; Insights views 76.8; Settings + subflows 73.7. Primary landing experiences outperform deep import, backup and bulk actions.

## 57 page and workflow scores
| Area | Page / workflow | UX /100 | Severity | Project QA/release gate |
|---|---|---:|---|---|
| Today | Dashboard / next check-in | 85 | P1 | Device QA pending |
| Body | Symptoms list | 79 | P1 | Device QA pending |
| Body | Concerns list | 78 | P1 | Device QA pending |
| Body | Skin log history | 76 | P1 | Device QA pending |
| Body | Prescription check-ins | 72 | P1 | Full E2E required |
| Body | Progress photos gallery | 72 | P0 | Photo restore gate |
| Protocols | AM routine | 82 | P1 | Device QA pending |
| Protocols | PM routine | 82 | P1 | Device QA pending |
| Protocols | Supplements | 74 | P1 | Full E2E required |
| Protocols | Hair routine | 77 | P2 | Device QA pending |
| Protocols | Prescription routine | 71 | P1 | Full E2E required |
| Protocols | Weekly schedule | 68 | P1 | Reorder persistence gate |
| Vault | Inventory | 83 | P1 | Device QA pending |
| Vault | Needs review | 78 | P1 | Device QA pending |
| Vault | Data cleanup | 69 | P1 | Bulk action safety gate |
| Vault | Smart Capture landing | 76 | P2 | Device QA pending |
| Vault | Import hub | 68 | P0 | Import and recovery gate |
| Vault | Routine compliance view | 65 | P1 | Definitions/evidence gap |
| Insights | Overview | 84 | P1 | Evidence QA pending |
| Insights | Patterns | 70 | P1 | Confidence language/evidence gate |
| Insights | Timeline | 80 | P2 | Device QA pending |
| Insights | Calendar | 73 | P1 | Date/timezone gate |
| Settings | Settings landing | 82 | P1 | Device QA pending |
| Settings | Appearance/theme | 84 | P2 | Accessibility QA pending |
| Settings | Professional summaries launcher | 80 | P1 | E2E required |
| Settings | Doctor Summary setup | 79 | P1 | E2E required |
| Settings | Doctor Summary confirm | 74 | P1 | Security gate |
| Settings | Doctor Summary result | 65 | P0 | Security gate |
| Settings | Doctor View | 75 | P1 | E2E required |
| Settings | Doctor Export builder | 72 | P1 | E2E required |
| Settings | JSON backup export | 73 | P0 | Photo restore gate |
| Settings | JSON backup import | 58 | P0 | Photo restore gate |
| Settings | Setup / Sample Preview | 75 | P1 | Data isolation gate |
| Settings | Reset browser data | 65 | P0 | Destructive action/rollback gate |
| Settings | Help & version history | 76 | P2 | Device QA pending |
| Onboarding | Welcome / first-run setup | 72 | P1 | Isolation/data protection gate |
| Product | Product details | 76 | P1 | Device QA pending |
| Product | Add/Edit product sheet | 69 | P1 | Form QA gate |
| Product | Product review / decision | 72 | P2 | Device QA pending |
| Product | Product journal note | 69 | P2 | Data QA pending |
| Product | Product actions sheet | 75 | P1 | Device QA pending |
| Body forms | Log/Edit symptom sheet | 74 | P0 | Photo cancel/save gate |
| Body forms | Add/Edit concern sheet | 72 | P0 | Photo cancel/save gate |
| Body forms | Skin check-in sheet | 75 | P1 | Form QA pending |
| Body forms | Progress photo editor/viewer | 66 | P0 | Photo persistence gate |
| Body forms | Rx check-in editor | 73 | P1 | E2E required |
| Body forms | Rx check-in history detail | 72 | P1 | E2E required |
| Protocols forms | Add/Edit routine step | 72 | P1 | Reorder/data QA |
| Protocols forms | Routine template picker/review | 66 | P1 | E2E required |
| Protocols forms | Supplement add/template search | 72 | P1 | Search QA pending |
| Protocols forms | Bulk supplement import | 62 | P1 | Import/recovery gate |
| Vault tools | Advanced filters and sorting | 68 | P1 | Form/category filter bug |
| Vault tools | CSV import mapping and preview | 62 | P0 | Import/recovery gate |
| Vault tools | Smart Capture camera/manual editor | 70 | P1 | Photo/permission gate |
| Vault tools | Cleanup bulk actions | 59 | P1 | Mutation preview/undo gate |
| Shared overlays | Reminder editor | 72 | P2 | Form QA pending |
| Shared overlays | Delete / confirm dialogs | 73 | P1 | Recovery QA pending |

## Product/project-management maturity (SEPARATE rubric)
- Requirements/traceability: 78/100. Governance, LUM IDs and acceptance exist; completeness uneven.
- Branch/change control: 88/100. Production main protected and feature PRs staged.
- Automated QA/reproducibility: 59/100. 80/80 prior isolated Beta7 checks and 37 current render/open checks, but real workflow QA incomplete.
- Data portability and rollback: **34/100**. Actual clean-origin IndexedDB photo restore and failure rollback not verified.
- Security/privacy: **40/100**. Targeted text escaping and preview guards; remaining dynamic HTML and writes require exhaustive testing.
- Accessibility/device: 47/100. Narrow-width and contrast improvements, physical VoiceOver/200% resize not verified.
- Preview/deployment controls: 84/100. Cloudflare preview SHA exists; production release is not approved.
**Overall unweighted delivery maturity: 61.4/100 (D).** This metric is a reviewer maturity snapshot, not release proof; P0 blockers override the average.

## Critical code-level findings (fix before production)
1. Doctor Summary confirmation/result constructs HTML with dynamic saved product names/fields rather than escaping values, unlike some other hardened views. Treat as an injection risk; add hostile synthetic-data regression. File root index.html, renderDocSummaryConfirm/renderDoctorSummaryResult.
2. Vault filter sheet uses the same _vaultFilterCat state for both Category and Form; applyVaultFilters compares it with product category. Form filtering therefore cannot be relied on; separate state and regression for Prescription/Supplement form.
3. JSON photo portability is still unverified in a real cross-origin IndexedDB browser, despite simulated unit paths. Clean HTTPS origin restore with photo counts/bytes/IDs is a release gate.
4. Data Cleanup auto-assign and bulk finish actions deserve preview, count, confirmation and undo or reliable recovery.
5. Weekly protocol reorder may render without exceptions, but iPhone touch/keyboard persistence still needs real tests.
6. In Insights, “High Confidence” labels must be backed by transparent methods and caveats; observational trends are not proof of causes.

## QA evidence and limitations
**PASS AUTOMATED (current audit):** 37/37 distinct render/open smoke checks (22 navigation main/subviews + 15 modals), Chromium 390px dark, fictional Sample Preview, mocked localStorage, no unhandled exceptions. This is not a Save/Delete/Import test.
**PASS AUTOMATED (prior docs):** 80/80 isolated Beta7 screen/width/theme+interaction tests, not rerun here.
**NOT TESTED:** actual Beta7 iPhone Safari/VoiceOver; genuine IndexedDB cross-origin photo restore, quotas, full CRUD, OS print/share, 200% zoom, Core Web Vitals and full security regression. Production main unchanged.

## Recommended iteration sequence
P0 photo/data restore proof and Doctor Summary output safety; P1 category vs form filter fix, weekly reorder, auto-cleanup confirmation, pattern evidence definition, mobile focus/controls; then user-tested UI refinement. Per-page individual strengths, gaps and acceptance tests are available in the separate detailed downloadable gradebook prepared in the current conversation.

## Handoff
No app code touched. Record this grading and requirements in docs-only draft PR from Beta7. Re-evaluate UX grades after usability observations, not merely a change in CSS. Do not merge into production without user authorization.