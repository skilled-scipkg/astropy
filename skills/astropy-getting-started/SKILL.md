---
name: astropy-getting-started
description: This skill should be used when users ask about getting started in astropy; it prioritizes documentation references and then source inspection only for unresolved details.
---

# astropy: Getting Started

## High-Signal Playbook

### Route conditions
- Use this skill for first-week usage questions across units, time, tables, coordinates, and WCS.
- Route installation/compiler/environment failures to `astropy-build-and-install`.
- Route deep modeling decisions to `astropy-inputs-and-modeling`, and workflow orchestration to `astropy-simulation-workflows`.
- Route version-specific behavior to `astropy-whatsnew` or unreleased fragment checks to `astropy-changes`.

### Triage questions
- Which core object is central right now: `Quantity`, `Time`, `QTable` or `Table`, `SkyCoord`, or `WCS`?
- Must physical units remain attached throughout the workflow?
- Are frame/time-scale transforms required (e.g., ICRS->FK5, UTC->TT)?
- Is data local/package data/remote (IERS or network implications)?
- Is this exploratory analysis or reproducible pipeline code?
- What is the smallest output that proves the path is correct?

### Canonical workflow
1. Pick the subsystem from the user guide map (`docs/index_user_docs.rst`).
2. Start with unit-aware values (`docs/units/index.rst`).
3. Parse times with explicit format/scale (`docs/time/index.rst`).
4. Create coordinates with explicit frame and units, then transform (`docs/coordinates/index.rst`).
5. Keep physical columns in `QTable` instead of plain `Table` when possible (`docs/table/index.rst`).
6. Validate one round-trip conversion before scaling to arrays/catalogs.
7. If unclear after docs, move to `references/source_map.md` and inspect targeted implementations.

### Minimal working example
```python
from astropy import units as u
from astropy.coordinates import SkyCoord
from astropy.time import Time
from astropy.table import QTable

coord = SkyCoord("00h42m30s", "+41d12m00s", frame="icrs")
obs_time = Time("2010-01-01T00:00:00", format="isot", scale="utc")
speed = (15.1 * u.m / (32.0 * u.s)).to(u.km / u.h)

row = QTable({"time": [obs_time], "ra": [coord.ra], "dec": [coord.dec], "speed": [speed]})
print(row)
```

### Pitfalls and fixes
- Missing coordinate angle units: provide `Quantity` inputs or `unit=` in `SkyCoord` (`docs/coordinates/index.rst`).
- Time-scale ambiguity: always set input `scale` and convert explicitly (`docs/time/index.rst`).
- Unit-aware math lost in plain tables: use `QTable` for physical columns (`docs/table/index.rst`).
- Broadcast errors in frame transforms: align shapes before `transform_to` (`docs/coordinates/frames.rst`).
- Unexpected Earth-rotation data fetches: account for IERS access/caching (`docs/coordinates/index.rst`).

### Convergence and validation checks
- Verify types/metadata at each step (`Quantity.unit`, `Time.scale`, frame name).
- Confirm transformed values remain physically plausible (ranges, signs, units).
- Confirm table operations preserve intended units and column types.
- If behavior still diverges from docs, inspect source entry points below before broad code search.

## Scope
- Handle questions about initial setup, quickstarts, and core concepts.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/units/index.rst`
- `docs/uncertainty/index.rst`
- `docs/timeseries/index.rst`
- `docs/stats/index.rst`
- `docs/modeling/index.rst`
- `docs/wcs/index.rst`
- `docs/time/index.rst`
- `docs/table/index.rst`
- `docs/nddata/index.rst`
- `docs/development/quickstart.rst`
- `docs/cosmology/index.rst`
- `docs/coordinates/index.rst`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- Use tutorials/examples as executable usage patterns when available.
- Use tests as behavior or regression references when available.
- If ambiguity remains after docs, inspect `references/source_map.md` and start with the ranked source entry points.
- Cite exact documentation file paths in responses.

## Tutorials and examples
- `docs/nddata/examples`
- `docs/wcs/examples`

## Test references
- `astropy/tests`
- `docs/changes/tests`

## Optional deeper inspection
- `astropy`
- `cextern`

## Source entry points for unresolved issues
- `astropy/visualization/wcsaxes/utils.py`
- `astropy/visualization/wcsaxes/coordinates_map.py`
- `astropy/timeseries/periodograms/lombscargle/utils.py`
- `astropy/timeseries/periodograms/lombscargle/implementations/utils.py`
- `astropy/wcs/utils.py`
- `astropy/units/utils.py`
- `astropy/time/utils.py`
- `astropy/modeling/utils.py`
- `astropy/cosmology/units.py`
- `astropy/coordinates/builtin_frames/utils.py`
- `astropy/table/_np_utils.pyx`
- `astropy/io/fits/hdu/table.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" astropy cextern`).
