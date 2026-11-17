# DARMO Title to KML

Standalone web page for the DAR Municipal Offices (DARMO): enter a title's technical description, check the closure on the satellite map, and download the lot as a **KML** file for Google Earth. It is a copy of the Survey Unit's *Title to Shapefile* page (ACE Workbench), with the same interface. It is not part of the Survey Unit web app.

## How to use

1. Open **https://acemllabore-eng.github.io/darmo-title-to-kml/** in Chrome or Edge. No installation, no sign-in. (Or download this repository and open `index.html`; keep `vendor/` beside it.)
2. Add your tie points once with **+ CSV** (columns: name or ID, N, E; optional survey, municipality, datum). They stay in that browser only. Or press **Manual** and type the tie point N/E.
3. Enter the TD (type it, paste the TD text, load a JSON, or import a filled E2C workbook), pick the tie point, check the closure.
4. Press **Export KML (.kml)** for one lot, or add lots to the batch and press **Export batch KML (.kml)** for one file with all of them.

Satellite imagery needs internet. Without it the lot is drawn on a plain grid; the KML is not affected.

## What the KML holds

- One folder per lot, in batch order.
- The lot polygon in WGS84 (longitude, latitude; 9 decimals), named `Lot <no> · <title no.>`, with title no., lot no., survey no., computed area, area on the TD, tie point, tie datum, closure and number of corners (shown in the Google Earth balloon and kept as KML data fields).
- The numbered corners and the tie point as points.

Corners are computed from the tie point grid (PRS92, or Luzon 1911 converted through WGS84) with the same math and datum parameters as the Survey Unit page. Before the download, the page reads the KML back and checks that every corner converts back to within 1 cm of its computed PRS92 position and that the area matches within 0.1 sq m.

## Differences from the Survey Unit page

- Exports KML instead of a zipped shapefile; no corners CSV.
- No E2C workbook export. Importing a filled E2C workbook still works.
- No title OCR (same as the Survey Unit page).

## Files

- `index.html`: the page.
- `vendor/`: Leaflet 1.9.4, proj4js 2.12.1, fflate (E2C import), This public copy has no built-in tie point list; add tie points from a CSV.

Everything runs in the browser: nothing typed into the page is sent anywhere. Only the satellite imagery is loaded from Esri.
