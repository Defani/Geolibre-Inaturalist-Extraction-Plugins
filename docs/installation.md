# Installation

## Requirements

- GeoLibre 0.9.0 or newer.
- The **MapLibre** renderer. The plugin declares `engines: ["maplibre"]` and uses
  the map object directly, which is not available on the Cesium globe or the
  Mapbox renderer.

## From the GeoLibre marketplace

Once the entry in [`marketplace/registry-entry.json`](../marketplace/registry-entry.json)
is merged into [`opengeos/geolibre-plugins`](https://github.com/opengeos/geolibre-plugins),
open **Settings → Manage Plugins** in GeoLibre and install **iNaturalist
Extractor** from the list.

## From a zip file

Package the three plugin files with `plugin.json` at the **root of the zip**
(no wrapping folder), the same layout the packaging script of
[geolibre-nasa-opera](https://github.com/opengeos/geolibre-nasa-opera) produces.

macOS / Linux:

```bash
cd geolibre-inaturalist-extractor
zip ../geolibre-inaturalist-extractor-1.3.0.zip plugin.json index.js style.css
```

Windows (PowerShell):

```powershell
cd geolibre-inaturalist-extractor
Compress-Archive -Path plugin.json, index.js, style.css -DestinationPath ..\geolibre-inaturalist-extractor-1.3.0.zip
```

Then in GeoLibre: **Settings → Manage Plugins → Settings → Install from file**
and pick the zip. Zip files are ignored by `.gitignore`, so they are never
committed by accident.

## From a manifest URL

Serve the contents of `geolibre-inaturalist-extractor/` from any static host and
point GeoLibre at the URL of `plugin.json`. For the web build the host has to
allow cross-origin requests (CORS), as the geolibre-nasa-opera docs also note.
