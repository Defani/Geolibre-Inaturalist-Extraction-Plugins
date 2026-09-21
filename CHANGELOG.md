# Changelog

The format is based on [Keep a Changelog](https://keepachangelog.com/), and this
project adheres to [Semantic Versioning](https://semver.org/).

## [Unreleased]

## [1.4.0] - 2026-09-21

Changes from the review of opengeos/geolibre-plugins#57.

### Fixed

- The toolbar button had almost no contrast in dark mode: its icon inherited the
  app's near-white foreground colour but sits on MapLibre's white control
  background. The icon is now dark (`#333` on `#fff`, about 12.6:1) like the
  neighbouring map buttons, with a visible keyboard focus ring.

### Changed

- Photos are no longer one `photos` column holding a JSON list. Each observation
  now has `photoCount`, `photo1` ... `photo5` (a plain full-size photo URL each,
  `null` when unused) and `photoAttribution`, so attribute tables and exports
  show one link per photo. The click popup reads these columns; layers saved
  with v1.3.x still open their popups.
- In the popup, each photo thumbnail is now a real link to the full-size photo.
- New icon: a raven (Material Symbols) replaces the magnifier-and-paw glyph.
- Sidebar: every section heading now has an icon, and the explanatory sentence
  under each heading or field is gone. The same text is kept as a tooltip on
  the heading / field label.

### Added

- Icons are Google's Material Symbols (Apache-2.0), inlined as SVG paths, so no
  web font or CDN request is needed.

## [1.3.1] - 2026-09-20

### Fixed

- *Max observations* is now enforced exactly. Values above 200 that are not a
  multiple of 200 used to fetch and add up to a full extra page (for example
  250 fetched up to 400). Pages are now sized evenly and the result is trimmed
  to the limit, which also avoids over-fetching from the iNaturalist API.
- A request that never answers no longer leaves the panel stuck on
  "Fetching" with the button disabled. Each iNaturalist request now times out
  after 30 s and reports it; closing the plugin still cancels the request.

### Changed

- Requires GeoLibre 3.0.0 or newer (was 0.9.0): older versions do not provide
  all the host APIs used for the map-view and layer-extent modes.
- The message shown when *Ignore the Area* is used without a narrowing filter
  now lists exactly which filters count (species or iconic taxa, taxon ID,
  place, project, observer, keyword).
- Photo links are only used when they are http(s) URLs.
- Removed an unused internal counter.

## [1.3.0]

### Features

- Fetch georeferenced iNaturalist observations for the current map view or the
  extent of the selected layer, added as a GeoJSON layer.
- Filters: date range (off by default), species / iconic taxa, observer
  usernames, free-text keyword, and a quality-grade dropdown.
- Advanced filters: taxon ID, place ID, photo license, project, annotation
  (term and value) and an *Ignore the Area* switch.
- Click popup with species, observer, date, quality grade and iconic taxon, plus
  up to three photo thumbnails when the observation has photos.
- Paged requests (200 per page, about 250 ms apart) with a 10 to 2000
  observation limit.

[Unreleased]: https://github.com/Defani/Geolibre-Inaturalist-Extraction-Plugins/compare/v1.3.1...HEAD
[1.3.1]: https://github.com/Defani/Geolibre-Inaturalist-Extraction-Plugins/compare/v1.3.0...v1.3.1
[1.3.0]: https://github.com/Defani/Geolibre-Inaturalist-Extraction-Plugins/releases/tag/v1.3.0
