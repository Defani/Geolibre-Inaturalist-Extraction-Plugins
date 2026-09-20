# Changelog

The format is based on [Keep a Changelog](https://keepachangelog.com/), and this
project adheres to [Semantic Versioning](https://semver.org/).

## [Unreleased]

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

[Unreleased]: https://github.com/Defani/Geolibre-Inaturalist-Extraction-Plugins/compare/v1.3.0...HEAD
[1.3.0]: https://github.com/Defani/Geolibre-Inaturalist-Extraction-Plugins/releases/tag/v1.3.0
