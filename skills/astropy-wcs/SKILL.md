---
name: astropy-wcs
description: This skill should be used when users ask about wcs in astropy; it prioritizes documentation references and then source inspection only for unresolved details.
---

# astropy: Wcs

## High-Signal Playbook

### Quick-start command
```bash
python - <<'PY'
import numpy as np
from astropy.wcs import WCS

w = WCS(naxis=2)
w.wcs.crpix = [24.0, 24.0]
w.wcs.cdelt = np.array([-0.05, 0.05])
w.wcs.crval = [0.0, -30.0]
w.wcs.ctype = ["RA---TAN", "DEC--TAN"]
pix = np.array([[20.0, 30.0]])
world = w.wcs_pix2world(pix, 0)
pix_back = w.wcs_world2pix(world, 0)
print(float(np.max(np.abs(pix_back - pix))))
PY
```

### Required inputs
- FITS/WCS header fields (projection, reference pixel/value, scale).
- Pixel/world coordinate samples for smoke validation.
- Allowed numeric error tolerance for round-trip transforms.

### Validation checkpoints
- Confirm WCS object initializes without header warnings/errors.
- Run pixel->world->pixel round-trip and check residual against tolerance.
- Validate axis ordering/units before overlaying or slicing datacubes.

## Scope
- Handle questions about documentation grouped under the 'wcs' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/wcs/history.rst`
- `docs/wcs/validation.rst`
- `docs/wcs/relax.rst`
- `docs/wcs/supported_projections.rst`
- `docs/wcs/note_sip.rst`
- `docs/wcs/loading_from_fits.rst`
- `docs/wcs/references.txt`
- `docs/wcs/references.rst`

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
- `astropy/wcs/wcs.py`
- `astropy/wcs/utils.py`
- `astropy/wcs/wcsapi/fitswcs.py`
- `astropy/wcs/wcsapi/high_level_api.py`
- `astropy/wcs/src/sip_wrap.c`
- `astropy/wcs/src/sip.c`
- `astropy/wcs/src/astropy_wcs_api.c`
- `astropy/wcs/tests/test_wcs.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" astropy cextern`).
