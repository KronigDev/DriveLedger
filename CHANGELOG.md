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

- All user-visible "LubeLogger" strings now read "DriveLedger" (page titles, PWA name,
  About section, report footers, email subject/body translations, API docs page,
  console banner). Functional identifiers are untouched for drop-in compatibility:
  `LUBELOGGER_*` environment variables, config keys, translation keys, cookie names,
  database schema and API routes are identical to upstream.
- Restyled every view: navigation, garage grid, record tables, record modals, settings,
  calendar, planner kanban, kiosk mode, reports, login pages, admin and API docs pages.
- Chart.js theming: brand-aligned categorical palette, status palette for reminder
  urgency, smooth green-to-red cost ramp, theme-aware axis/legend/grid colors,
  rounded bars and surface-colored segment gaps.
- `docker-compose.yml` now builds the image locally (`build: .`, tagged
  `driveledger:latest`) since DriveLedger does not publish a container image.
- Settings About section credits the upstream LubeLogger project and links to it.

### Unchanged (by design)

- Controllers, business logic, models, database access, API routes and form behavior.
- All element IDs, `data-*` attributes and functionally used CSS class names.
- Existing translations keep working; non-English languages still download from the
  upstream community translation repository.
