# Cloudflare Pages Plan
Status: planned; not yet connected/verified. GitHub: Deidrajw/Lumina, main, root index.html.

## Initial setup
Cloudflare dashboard > Workers & Pages > Create application > Pages > Import existing Git repository. Authorize/access Deidrajw/Lumina. Set production branch `main`, no framework, no build needed (blank build command or `exit 0`), static output directory repository root (validate `.` for this configuration), root directory repo root. Verify Pages deploy serves top-level index.html. Configure preview builds for non-main branches and confirm branch controls. Keep branch approval/PR review before merging code.

Official: https://developers.cloudflare.com/pages/framework-guides/deploy-anything/ and https://developers.cloudflare.com/pages/configuration/git-integration/

## Before a live address migration
Current records are saved in browser localStorage/IndexedDB and WILL NOT automatically appear on a new Pages hostname. Maintain old address; create a securely stored backup; repair and test photo restore on a clean target origin; verify links and full history before retiring old origin. Never publish private backups in GitHub.

## Release / rollback
Feature branch -> PR -> Cloudflare preview -> QA -> approval -> merge to main -> verify live URL and commit. Capture build ID, app version, screenshots/test results and rollback SHA. To roll back code, revert commit on main; this does NOT restore deleted local browser data. Never claim deploy succeeded without checking Cloudflare.