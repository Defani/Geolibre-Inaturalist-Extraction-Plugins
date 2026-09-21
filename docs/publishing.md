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
- [ ] `minGeoLibreVersion` in the registry entry is the lowest GeoLibre version that
      provides every host API the plugin uses.

## First submission

1. Fork [`opengeos/geolibre-plugins`](https://github.com/opengeos/geolibre-plugins)
   and create a branch.
2. Copy `plugin.json`, `index.js` and `style.css` from
   `geolibre-inaturalist-extractor/` into
   `plugins/geolibre-inaturalist-extractor/` in the fork.
3. Whitespace-minify the bundle. In the fork clone run:

   ```bash
   npm ci
   npm run minify         # rewrites plugins/**/*.js in place (whitespace only)
   npm run minify:check   # what CI checks
   ```

   The marketplace's *Minify plugin bundles* workflow requires committed bundles to be
   minified. On a branch in the marketplace repo it pushes the result for you; on a
   **fork** it cannot, so the check fails until you commit the minified file (or
   download the `minified-bundles` artifact from the failed run and commit that). Keep
   the readable source in this repository; only the copy in the marketplace is minified.
4. Add the object from [`marketplace/registry-entry.json`](../marketplace/registry-entry.json)
   to the `plugins` array of `plugin-registry.json`. Its `manifestUrl` is relative
   to the marketplace repo (`plugins/geolibre-inaturalist-extractor/plugin.json`).
5. Open a pull request. The marketplace repo runs checks on pull requests (lint,
   plugin validation, minify check, and a preview build); fix anything they report.

## Updating a published plugin

1. Bump `version` in `plugin.json`, in `index.js` and in the registry entry
   (the marketplace expects the manifest and the registry entry to agree).
2. Copy the changed files into `plugins/geolibre-inaturalist-extractor/`, run
   `npm run minify` again, and update the `version` (and `description`, if it changed)
   of the entry in `plugin-registry.json`.
3. Open a pull request.

## Entry fields

| Field                | Value                                                    |
| -------------------- | -------------------------------------------------------- |
| `id`                 | `geolibre-inaturalist-extractor`                         |
| `name`               | `iNaturalist Extractor`                                  |
| `categories`         | `["Data"]`                                               |
| `minGeoLibreVersion` | `3.0.0`                                                  |
| `homepage`           | this repository                                          |
| `manifestUrl`        | `plugins/geolibre-inaturalist-extractor/plugin.json`     |
