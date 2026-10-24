# Known Bugs — pending current-build reproduction
| ID | Severity | Evidence / issue | Status |
|---|---|---|---|
| LUM-BUG-001 | Critical | v0.9.4 `exportData()` embeds IndexedDB `_photoBlobs`; `importData()` only restores `KEYS` (code inspected). Photos may be unavailable after restore on another origin. | Open: reproduce |
| LUM-BUG-002 | High | Previous reports: concern/symptom save failed when attaching a photo; photo-storage refactor exists; requires device re-test. | Re-test |
| LUM-BUG-003 | High | Previous reports: supplement search/template picker sometimes blank after typing. | Re-test |
| LUM-BUG-004 | High | Historical: global search > product > edit loses detail screen. | Re-test |
| LUM-BUG-005 | High | Historical: progress photo lightbox lacks reliable exit. | Re-test |
| LUM-BUG-006 | High | Historical: protocol reorder does not work reliably on mobile. | Re-test |
| LUM-BUG-007 | High | Smart Capture must not falsely imply connected label OCR; verify actual behavior. | Audit |
| LUM-BUG-008 | Medium | Header/tab/bottom-nav overlaps and double scrolling on iPhone. | Re-test |
| LUM-BUG-009 | High | `clearAllData()` clears localStorage; IndexedDB photo cleanup not evident in handler. | Audit |

Bug template: ID / date / device / reproduction / expected / actual / severity / root cause / patch PR / regression evidence / status.