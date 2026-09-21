# Contributing

Thanks for considering a contribution. These are guidelines, not strict rules;
feel free to propose changes to this document in a pull request.

## Layout

The plugin lives in [`geolibre-inaturalist-extractor/`](geolibre-inaturalist-extractor/).
It has no build step: `index.js` is a self-contained ES module without imports,
so edit it directly. Everything else in the repository (docs, marketplace entry,
templates) supports it.

## Testing locally

1. Check the syntax: `node --check geolibre-inaturalist-extractor/index.js`.
2. Package and install the plugin as described in
   [docs/installation.md](docs/installation.md), then try a search in GeoLibre
   on the MapLibre renderer.

## Code guidelines

- Keep styles scoped under the `.geolibre-inat-*` prefix in `style.css` and keep
  them working in both light and dark themes.
- Keep the request limits (pages of at most 200, roughly 250 ms between pages,
  at most 2000 observations). They follow iNaturalist's API recommended
  practices; please do not raise them.
- Only send parameters that iNaturalist's observations endpoint documents.
- Do not copy code from other projects into the plugin. The projects listed in
  the README's credits are references only.

## Versioning

Use [Semantic Versioning](https://semver.org/). When you change the version,
update all of these together:

- `geolibre-inaturalist-extractor/plugin.json`
- the `version` exported by `geolibre-inaturalist-extractor/index.js`
- `marketplace/registry-entry.json`
- the version badge in `README.md`
- `CHANGELOG.md`

See [docs/publishing.md](docs/publishing.md) for getting a release into the
GeoLibre marketplace.

## License

By contributing you agree that your contribution is licensed under
GPL-2.0-or-later, like the rest of the project.
