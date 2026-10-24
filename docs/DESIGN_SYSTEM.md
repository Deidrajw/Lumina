# Visual Design System
Direction: quiet luxury, premium wellness/skincare journal, mature warm feminine; never clinical, cluttered, childish or neon. Source: current `index.html`, not stale visual docs.

Fonts: **Instrument Serif** for headings, **Manrope** for UI. Dark: background #13111a; panels #1c1925/#242130; text #ede8f4; mauve #b07eb8; warm bronze #c4957a; gold #c9a96e; lavender #8b7ec4. Light: background #f7f4f0 with theme token overrides.

Patterns: fixed bottom nav, sticky headings, rounded cards, compact tabs + overflow, bottom sheets with sticky safe-area footer, product slide-over, chips, rings, photo grids, lightbox and collapsible groups. Prefer progressive disclosure over density. Align chevrons/icons; sufficient contrast; roughly 44px touch targets; readable labels; no double scrolling or clipped safe areas. Test light/dark, narrow widths, long text and empty states.

## 2026-10-24 beta.5 candidate tokens and accessibility
Existing dark/light Lumina aesthetics and Instrument Serif/Manrope remain. Candidate metadata token dark tertiary #948ba9, dark secondary #b4acc5; light tertiary #6b6178. Main card/white contrast of tertiary ~5.37/5.82:1 respectively. Bottom labels >=11px, form/section headings >=12px, 44px Settings icon and peer tab targets, 16px form controls, browser zoom allowed, focus-visible outline, reduced-motion override. Role changes: primary nav aria-label, current page aria-current, Settings accessible label. No screen IA redesign in code. See docs/AUDIT_UIUX_FULL_2026-10-24.md for proposed patterns awaiting approval.


## 2026-10-24 approved IA implementation: Beta 6
Preserve Instrument Serif/Manrope and existing plum/mauve tokens. Today: primary check-in and quick actions before bounded scheduled progress; urgent reminders never hidden; old history behind native accessible details. Vault: context-first total/review/search, only secondary stock collapsed; status section controls are semantic buttons with aria-expanded/controls. Insights: primary observation and date range first; evidence, dated entries, secondary analysis expandable; never overclaim causality. Body/Protocols/Settings approved concept remains separate implementation scope. Do not replace shared data models or hide error/success states to achieve aesthetic goals.


## 2026-10-24 Beta7 Body/Protocols/Settings implementation
Preserve Instrument Serif/Manrope and dark/light Lumina tokens. Body primary log actions min 44px and advanced filters via native details; Protocols contextual count, visible Show all/Reorder touch actions with aria-pressed and unsupported supp mode disabled; Settings doctor vs backup separation and independent setup/destructive disclosures. No data model/renderer feature removed. True Safari/VoiceOver/focus state pending verification.
