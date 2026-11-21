# Lumina — Mandatory Chat Continuity Note
Updated: 2026-11-21. Reuse at the **bottom of every Lumina development response**, including no-change reviews and partial work. Keep it short in chat; keep durable dated details in docs/CONTINUITY_LOG.md.

### Continuity Note — YYYY-MM-DD
- **Version/status:** production version + SHA; candidate version + branch/commit/PR; PROPOSED / IMPLEMENTED / TESTED / DEPLOYED (distinguish).
- **Changed:** exact files, screens/functions, requirement IDs; what was completed in THIS chat.
- **Not changed:** production/main, data/schema/migrations, planned work excluded; note any exceptions.
- **Testing:** PASS (automated/manual), FAIL, BLOCKED, NOT TESTED, N/A; platform, evidence and docs/QA_REGRESSION.md entry; no unearned PASS.
- **Data and risks:** storage/IndexedDB impact, backups, known bugs, release blockers, rollback.
- **Need from user:** only actionable device test, screenshot (non-sensitive), design/merge approval, or 'nothing right now'.
- **Next exact step:** one concrete immediate action in priority order; link relevant GitHub docs/PR.

### Session close instructions
Append dated detailed handoff to CONTINUITY_LOG; prepend concise current pointer in PROJECT_STATE; append QA run to QA_REGRESSION (even for docs-only); update register/known bugs/changelog/release gates if relevant. Identify whether GitHub writes succeeded; if not, state plainly that the handoff is chat-only and needs committing. Never claim future automatic syncing across chats: next chat must read current repo.
