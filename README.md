# Ticket Designer v7 — Fresh Architecture

This package is a clean starting point built from the uploaded current system and the finalized architecture. Existing ticket/event designs and operational ticket records were intentionally excluded from the new Google Sheets.

## Final page roles
- `index.html` — staff login
- `dashboard.html` — staff operations: vouchers, check-in, walk-ins, reports
- `designer.html` — create/design event tickets
- `admin.html` — System Owner user/role management
- `batch.html?batch=...` — public secure voucher-set distribution
- `claim.html?voucher=...` — single voucher claim
- `v.html` — compatibility redirect only; no new links should use it

## Fresh Google Sheets
1. Import `TicketDesigner_Regional_Config_v7.xlsx` into a NEW Google Sheet.
2. Open Extensions → Apps Script and paste `backend/regional/Code.gs`.
3. Deploy as Web App: Execute as you; access Anyone.
4. Import `TicketDesigner_Workflow_v7.xlsx` into another NEW Google Sheet.
5. Paste `backend/workflow/Code.gs` into that workbook's Apps Script project.
6. Run `setRegionalConfigEndpoint('NEW_REGIONAL_EXEC_URL')` once from the Workflow Apps Script editor.
7. Deploy Workflow as Web App: Execute as you; access Anyone.
8. Update `assets/js/app-config.js` with both new `/exec` URLs.

## Data carried forward
Copied: Organization, chapter reference/branding/contact data, and non-event-specific administrator records.
Not copied: Existing Events, TicketTypes, event-specific Event Organizer rows, EventPermissions, old audit history, tickets, vouchers, batches, counters, check-ins, or workflow audit records.

## First event
With an empty Events table, an authorized System Owner, Regional Admin, or Chapter Admin can sign in. If no event is available, the landing page routes the user to `designer.html`. Enter the chapter code and a new Event ID when prompted, then save the event/ticket design.

## Social previews
- `/` → `admin-og.jpg`
- `dashboard.html` → `gate-og.jpg`
- `designer.html` → `config-og.jpg`
- `admin.html` → `admin-og.jpg`
- `batch.html` → `distribution-og.jpg`
- `claim.html` → `claim-og.jpg`

## Important
Do not copy the previous Apps Script deployment URLs into the new system. Deploy the fresh Google Sheets/backends first, then update `app-config.js`.
