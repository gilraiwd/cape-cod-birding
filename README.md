# Birding Console

A personal birding tracker built around one question: **of everything being reported nearby, what haven't I seen yet?**

It compares live eBird sightings against your life list and surfaces the gaps — especially rare and unseen species — on an interactive map and list view. No install, no build step, no server: it's a single self-contained HTML file that runs entirely in your browser.

## Features

- **Live eBird sync** — pulls recent and notable/rare sightings daily for any region(s) you configure, using your own free eBird API key. Also keeps eBird species links accurate via a live taxonomy sync, and links each sighting to the actual eBird checklist it came from.
- **Life lists** — upload your eBird life list export (My eBird → Download My Data) to automatically derive "seen" status. Upload more than one, label them, and switch between them — handy for sharing this site with someone else without your data overwriting theirs.
- **Interactive map** — every hotspot plotted and color-coded (unseen rare target / partially seen / fully seen), clustered by zoom level, with a Find Me button and a Home button that zooms to your active region.
- **Two list views** — *By Species* (one row per bird, every hotspot it's been reported at) or *By Sighting* (one row per report).
- **Filtering** — independent species and hotspot search, date range (24h/7d/30d/custom), region, and status (seen/unseen/rare/priority) filters, all combinable.
- **Hotspot cleanup** — hide hotspots you don't care about, or merge near-duplicate names (e.g. "Race Point" / "Race Point Beach" / "Race Point Light") with rename and unmerge support.
- **Region management** — track multiple regions at once; hide a region temporarily (e.g. while traveling) without deleting its data, or remove one permanently.
- **Import/export** — upload an eBird rare-alert report (.docx/.txt/.tsv) to merge in sightings manually, or export the current filtered view as CSV.
- **Installable PWA** — add it to your phone's home screen for an app-like experience.

## Getting started

1. **Host it.** The simplest option is GitHub Pages: push `index.html` to a repo, enable Pages in the repo settings, and it's live. It also works fine opened directly as a local file, or hosted anywhere that serves static files.
2. **Get a free eBird API key** at [ebird.org/api/keygen](https://ebird.org/api/keygen) (requires an eBird account).
3. Open the site → **Settings** → paste your API key, and add the region code(s) you want to track (see below).
4. Upload your life list under **Import** → Upload Life List CSV (from My eBird → Download My Data on eBird.org).
5. That's it — the app auto-syncs once a day when opened, or hit **Sync Now** in Settings any time.

### Finding a region code

Region codes follow eBird's own format: country (`US`), state/province (`US-MA`), or county (`US-MA-001`). The easiest way to find one is to browse to that area on [eBird's Explore page](https://ebird.org/explore) — the region code is in the URL.

## How it works / data & privacy

There is no backend. Everything — your sightings, life lists, hotspot data, and settings — lives in your browser's `localStorage`, scoped to wherever the file is hosted. Nothing is sent anywhere except direct calls to the eBird API (using your key) and Wikipedia (for species thumbnails).

This also means:
- Clearing your browser's site data for this page deletes everything. There's no cloud backup.
- If you host this on GitHub Pages and share the URL, anyone who opens it gets their *own* independent local copy of the app — they don't see your data, and you don't see theirs.
- Your eBird API key is stored in the page's default value in plain text if you leave it hardcoded in the file. Don't publish a copy of the file with your real key baked in as the default — set it in Settings instead, where it's saved to local storage, not the file itself.

## Known limitations

- **No automatic life list sync.** eBird's public API doesn't expose personal life lists — this isn't a gap in this app, it's a gap in what eBird makes available. The manual CSV upload is the only way, but it's quick (two clicks on eBird's site).
- **Region tagging only applies to eBird-synced data.** Sightings added manually or imported from a report file aren't tagged with a region automatically — hiding/filtering by region falls back to inferring it from other sightings at the same hotspot, but a hotspot that's *never* had an eBird-synced sighting can't be inferred and won't respond to region filters.
- **No true background sync.** As a static page with no server, syncing only happens when the app is actually open — "daily" sync means "checks whether it's been a day since the last time you opened it."
- **Unmerging a hotspot** restores it to its state right before the merge; anything added to the merged hotspot *after* merging has no original hotspot to return to and will be dropped if you later unmerge.

## Changelog

See the **ℹ️ About** button in the app itself for a running changelog and last-updated date.
