---
name: astropy-coordinates
description: This skill should be used when users ask about coordinates in astropy; it prioritizes documentation references and then source inspection only for unresolved details.
---

# astropy: Coordinates

## High-Signal Playbook

### Quick-start command
```bash
python - <<'PY'
import astropy.units as u
from astropy.coordinates import SkyCoord

c_icrs = SkyCoord(ra=10 * u.deg, dec=20 * u.deg, frame="icrs")
c_gal = c_icrs.galactic
c_back = c_gal.transform_to("icrs")
print(c_gal.l.deg, c_gal.b.deg, c_back.separation(c_icrs).arcsec)
PY
```

### Required inputs
- Coordinate values with explicit angle units.
- Source and target frame names (and `obstime`/`location` when required).
- Expected precision tolerance for round-trip checks.

### Validation checkpoints
- Confirm transformed coordinate frame is the intended target frame.
- Verify round-trip separation is within tolerance for the use case.
- Check broadcasting/shape alignment before batch transformations.

## Scope
- Handle questions about documentation grouped under the 'coordinates' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/coordinates/satellites.rst`
- `docs/coordinates/inplace.rst`
- `docs/coordinates/definitions.rst`

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
- `astropy/coordinates/sky_coordinate.py`
- `astropy/coordinates/baseframe.py`
- `astropy/coordinates/transformations/graph.py`
- `astropy/coordinates/transformations/function.py`
- `astropy/coordinates/representation/base.py`
- `astropy/coordinates/angles/core.py`
- `astropy/coordinates/earth.py`
- `astropy/coordinates/solar_system.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" astropy cextern`).
