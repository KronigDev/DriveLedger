# Changelog

All notable changes to DriveLedger are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

DriveLedger is a visual-redesign fork of [LubeLogger](https://github.com/hargata/lubelog).
Versions below describe DriveLedger releases; the underlying application functionality
tracks the upstream LubeLogger version noted per release.

## [1.0.0] - 2026-07-02

Based on LubeLogger 1.6.8. Functionality is unchanged from upstream; this release is a
complete visual redesign and rebranding.

### Added

- Central design system (`wwwroot/css/driveledger.css`): design tokens as CSS custom
  properties for color scales (derived from the logo's blue-to-green gradient), typography,
  spacing, radii, shadows and transitions, defined for both light and dark themes on top of
  Bootstrap 5.3's CSS-variable API.
- Fully maintained dark mode across every view, including modals, dropdowns, tables,
  date picker, tags input, SweetAlert2 dialogs, loading overlay and charts.
- Self-hosted Inter variable font (`wwwroot/fonts/`), no CDN dependency.
- Colorblind-validated chart palettes (light and dark variants) for the dashboard's
  pie, doughnut and bar charts; WCAG AA checked interactive colors.
- New DriveLedger branding assets: logo, wordmark, favicon, PWA icons (any + maskable),
  iOS splash screen, vehicle image placeholder and garage add-tile icon
  (filenames kept from upstream so config overrides keep working).
- PWA manifest metadata: name, description, theme and background colors.

### Changed

- Complete information-architecture redesign of the app shell: a fixed sidebar
  navigation on desktop (logo on top, vertical tab list, Settings and account
  pinned to the bottom) replaces the old horizontal top bar; pages get content
  headers (vehicle identity with edit action, garage/calendar/settings titles);
  the Settings page is regrouped into titled section cards (Appearance,
  Behavior, Fuel & Units, Automation, Modules, Visible Tabs, Backups, Server);
  the dashboard's headline numbers render as stat-tile cards. Mobile keeps the
  top bar + full-screen menu paradigm with the new page headers. The legacy
  collapse-tabs-into-dots overflow behavior was removed since a vertical nav
  cannot overflow; every tab stays visible and functional.

- All "LubeLogger" identifiers now read "DriveLedger": page titles, PWA name,
  About section, report footers, email subjects/bodies (translation keys and
  values), API docs page, console banner, internal CSS class names
  (`lubelogger-*` is now `driveledger-*`, `ll-responsive-table` is now
  `dl-responsive-table`, with all jQuery selectors updated in lockstep),
  environment variables and config keys (`LUBELOGGER_*` is now `DRIVELEDGER_*`),
  the iCal export `PRODID`, Docker/Traefik service names and the PostgreSQL
  compose credentials. The database schema, uploaded-file layout and API routes
  are identical to upstream, so existing data volumes keep working; only
  configured `LUBELOGGER_*` environment variables need a one-time rename.
- Restyled every view: navigation, garage grid, record tables, record modals, settings,
  calendar, planner kanban, kiosk mode, reports, login pages, admin and API docs pages.
- Chart.js theming: brand-aligned categorical palette, status palette for reminder
  urgency, smooth green-to-red cost ramp, theme-aware axis/legend/grid colors,
  rounded bars and surface-colored segment gaps.
- `docker-compose.yml` now builds the image locally (`build: .`, tagged
  `driveledger:latest`) since DriveLedger does not publish a container image.
- Settings About section credits the upstream LubeLogger project and links to it.
- The app reports version 1.0.0 (DriveLedger versioning) and the update check
  (`/api/version?checkForUpdate=true`) now queries DriveLedger releases instead
  of upstream LubeLogger releases.
- Branding asset files renamed from `lubelogger_*` to `driveledger_*` (all
  references updated: layout, PWA manifest, About page, defaults in
  `StaticHelper`); unused upstream `hargata_logo*.png` files removed.
- Outgoing webhook notifications (Discord format) now post as "DriveLedger"
  with the DriveLedger avatar.
- Removed the upstream marketing-site sources from `docs/` (the folder now only
  holds DriveLedger screenshots); removed unused upstream logo files.

### Unchanged (by design)

- Controllers, business logic, database access, API routes and form behavior.
- All element IDs and `data-*` attributes.
- Non-English languages still download from the upstream community translation
  repository. Because the handful of email-related translation keys were
  rebranded, those few strings fall back to English until the community files
  carry the new keys; everything else stays fully translated.
