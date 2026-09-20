# Publishing to the GeoLibre marketplace

The marketplace is the [`opengeos/geolibre-plugins`](https://github.com/opengeos/geolibre-plugins)
repository. A plugin is listed by a folder under `plugins/` plus an entry in
`plugin-registry.json`. This page is the checklist for submitting
`geolibre-inaturalist-extractor` and for later updates.

## Before you submit

- [ ] `version` is the same in `geolibre-inaturalist-extractor/plugin.json`, in the
      exports of `geolibre-inaturalist-extractor/index.js` and in
      `marketplace/registry-entry.json`.
- [ ] `id` and `name` in `plugin.json` match what `index.js` exports.
- [ ] `node --check geolibre-inaturalist-extractor/index.js` passes.
- [ ] The plugin loads in GeoLibre (install it from a zip, see
      [installation.md](installation.md)) and a search returns points with a popup.
- [ ] `CHANGELOG.md` and the version badge in `README.md` are updated.

## First submission

1. Fork [`opengeos/geolibre-plugins`](https://github.com/opengeos/geolibre-plugins)
   and create a branch.
2. Copy `plugin.json`, `index.js` and `style.css` from
   `geolibre-inaturalist-extractor/` into
   `plugins/geolibre-inaturalist-extractor/` in the fork.
3. Add the object from [`marketplace/registry-entry.json`](../marketplace/registry-entry.json)
   to the `plugins` array of `plugin-registry.json`. Its `manifestUrl` is relative
   to the marketplace repo (`plugins/geolibre-inaturalist-extractor/plugin.json`).
4. Open a pull request. The marketplace repo runs a CI preview on pull requests;
   fix anything it reports.

## Updating a published plugin

1. Bump `version` in `plugin.json`, in `index.js` and in the registry entry
   (the marketplace expects the manifest and the registry entry to agree).
2. Copy the changed files into `plugins/geolibre-inaturalist-extractor/` and update
   the `version` (and `description`, if it changed) of the entry in
   `plugin-registry.json`.
3. Open a pull request.

## Entry fields

| Field                | Value                                                    |
| -------------------- | -------------------------------------------------------- |
| `id`                 | `geolibre-inaturalist-extractor`                         |
| `name`               | `iNaturalist Extractor`                                  |
| `categories`         | `["Data"]`                                               |
| `minGeoLibreVersion` | `0.9.0`                                                  |
| `homepage`           | this repository                                          |
| `manifestUrl`        | `plugins/geolibre-inaturalist-extractor/plugin.json`     |
