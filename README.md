# Material Behaviour Explorer

**Live tool:** https://arashnassirpour.com/material-behaviour-explorer/

An interactive stress-strain behaviour explorer for structural materials. It plots the full constitutive response for concrete, reinforcing steel, structural steel, timber, masonry and FRP, and lets you step through the curve, run cyclic loading, and compare multiple materials on one chart.

## Current engineering scope

- Concrete: Popovics/Thorenfeldt-style compression envelope with tension softening, driven by standard presets (e.g. C30) or custom inputs.
- Reinforcing and structural steel: elastic-plastic response with a continuous, code-checked yield transition (e.g. S355).
- Timber, masonry and FRP: material-specific envelopes, including linear-then-rupture behaviour for FRP.
- Custom material input: user-defined stress-strain points, with validation that rejects non-monotonic strain.
- Loading modes: monotonic envelope and cyclic loading, with adjustable amplitude, cycle count and pattern (e.g. increasing).
- Side-by-side comparison of multiple materials/presets on the same chart.
- SI and US unit toggle (MPa/ksi) with round-trip-consistent conversion.
- Chart export to PNG, and data export to CSV and JSON.
- Dark/light theme, keyboard-navigable chart trace stepping, and a guided example for first-time users.
- Built-in scientific self-check suite that verifies peak points, continuity at yield, tension-softening cutoffs, and preset validity every time the page loads.

## Verification

The page runs its own regression suite in the browser on load (`runScientificSelfTests`), covering peak-stress accuracy, yield continuity, tension-softening cutoffs, custom-point validation, unit round-trips, and finite/valid output for every built-in preset. Results are shown live in the app's self-test badge; failures are also logged to the browser console.

## Local development

This is a single self-contained static HTML file with no build step and no dependencies. To work on it locally:

```bash
open index.html
```

or serve the folder with any static file server, e.g.:

```bash
python -m http.server
```

## Repository layout

| Path | Responsibility |
|---|---|
| `index.html` | Entire application: layout, styling, material models, chart rendering, UI logic and self-tests |

## Deployment

This is a static, dependency-free page. The live version is published from the `arashnass.github.io` hub repository under `/material-behaviour-explorer/`, so this repo is the source-of-truth codebase, not the live deployment target.

## Important limitation

This software is not a substitute for professional engineering judgement. Material models, presets, and all results must be independently verified by a qualified structural engineer before use in design.

## Licence

Copyright (C) 2026 Arash Nassirpour.

Licensed under the GNU Affero General Public License v3.0 only (`AGPL-3.0-only`). See [LICENSE](LICENSE).
