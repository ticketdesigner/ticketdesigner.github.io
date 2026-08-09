# Ticket Designer v7 Architecture

## Staff roles
System Owner: full system and user management.
Regional Admin: all event operations/configuration in organization.
Chapter Admin: event operations/configuration in assigned chapter.
Event Organizer: assigned event operations/configuration.
Gate Staff: check-in only.

## Public actors
Voucher Distributor: bearer access to one `batch.html?batch=...` voucher set.
Ticket Recipient: bearer access to one `claim.html?voucher=...` voucher.

## Progression
`admin.html` grants role/scope → staff logs in at `index.html` → `dashboard.html` for operations → `designer.html` for event/ticket design → generate one voucher to `claim.html`, or multiple vouchers to `batch.html` → individual recipients use `claim.html` → Gate Staff checks tickets in from `dashboard.html`.

## Backends
Regional Config is the source of truth for organizations, chapters, events, ticket tiers, administrators, branding, and role/scope authorization.
Workflow is the source of truth for generated vouchers, batches, issued tickets, counters, check-ins, and operational audit records.
