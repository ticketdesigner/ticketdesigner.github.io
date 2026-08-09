
## Production host

This repository is a GitHub user site and the application is hosted at the repository root:

`https://ticketdesigner.github.io/`

Upload the *contents* of this folder directly to the root of `ticketdesigner/ticketdesigner.github.io`. Do not create an extra `slppna/` directory.

The core public routes are:

- Staff login: `https://ticketdesigner.github.io/`
- Voucher gateway: `https://ticketdesigner.github.io/v.html?voucher=...`
- Voucher/staff claim operations: `https://ticketdesigner.github.io/claim.html`
- Ticket configuration: `https://ticketdesigner.github.io/config.html`
- System-owner administration: `https://ticketdesigner.github.io/admin.html`

# Ticket Designer GitHub Pages Application

This public folder keeps the proven SLPP Tickets workflow/UI and replaces only the final ticket artwork generation with the SLPP North America regional master renderer.

## Upload hierarchy

Copy the contents of this folder directly into the repository root of `ticketdesigner/ticketdesigner.github.io`.

```text
ticketdesigner.github.io/
└── 
    ├── .nojekyll
    ├── index.html
    ├── claim.html
    ├── v.html
    ├── assets/
    │   └── js/
    │       ├── app-config.js
    │       └── ticket-renderer.js
    └── tickets/
        ├── azc/skyline-bg.png
        ├── canc/skyline-bg.png
        ├── casc/skyline-bg.png
        ├── drc/skyline-bg.png
        ├── dvc/skyline-bg.png
        ├── flc/skyline-bg.png
        ├── gac/skyline-bg.png
        ├── iac/skyline-bg.png
        ├── ilc/skyline-bg.png
        ├── mnc/skyline-bg.png
        ├── ndc/skyline-bg.png
        ├── nec/skyline-bg.png
        ├── njc/skyline-bg.png
        ├── nyc/skyline-bg.png
        ├── ohc/skyline-bg.png
        ├── swc/skyline-bg.png
        ├── txdc/skyline-bg.png
        ├── txhc/skyline-bg.png
        ├── vac/skyline-bg.png
        └── wdc/skyline-bg.png
```

## Website URLs

Default New York page:
`https://ticketdesigner.github.io/claim.html?org=SLPPNA&chapter=NYC&event=NYC-2026-INAUGURATION`

New England page:
`https://ticketdesigner.github.io/claim.html?org=SLPPNA&chapter=NEC&event=NEC-2026-INAUGURATION`

## Two backend roles

- `workflowEndpoint` = the existing SLPP Tickets backend. It remains responsible for claims, vouchers, distribution, admin unlock, check-in, walk-ins and reporting.
- `ticketConfigEndpoint` = the regional configuration endpoint. It is read only when building the actual ticket image, supplying chapter/event/tier/skyline/colors.

Both URLs are in `assets/js/app-config.js`.

## Important

Do **not** put the private Apps Script source or spreadsheets from the companion private setup packet in a public GitHub repository. The legacy workflow backend contains administrator passcodes.


## Updated design rules

- Ticket configuration remains private in Google Sheets / Apps Script. No public configuration interface is exposed.
- Public URLs support `org`, `chapter`, and `event` filters.
- The ticket renderer supports a dynamic number of tiers and pricing modes `FIXED`, `DONATION`, and `FREE` when supplied by the backend.
- The chapter skyline is rendered about 25% larger than the prior version for stronger visual presence.
- System-owner / event-organizer permissions and voucher-generation expiration are backend authorization concerns and should not be stored in this public repository.


## Ticket Configuration UI
Open `config.html?org=SLPPNA&chapter=NYC&event=NYC-2026-INAUGURATION`. The page requires an authorized owner/event-organizer passcode from the ticket configuration Apps Script. It edits ticket text, dynamic tiers, skyline size, and an optional event-specific logo. Chapter default logos live under `tickets/<chapter>/logo.png`.
