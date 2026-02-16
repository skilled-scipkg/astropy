---
name: astropy-analysis-and-output
description: This skill should be used when users ask about analysis and output in astropy; it prioritizes documentation references and then source inspection only for unresolved details.
---

# astropy: Analysis and Output

## High-Signal Playbook

### Quick-start command
```bash
python - <<'PY'
import numpy as np
from astropy.visualization import ImageNormalize, PercentileInterval, SqrtStretch
from astropy.wcs import WCS

data = np.arange(10000.0).reshape(100, 100)
norm = ImageNormalize(data, interval=PercentileInterval(99.5), stretch=SqrtStretch())
wcs = WCS(naxis=2)
wcs.wcs.crpix = [50.0, 50.0]
wcs.wcs.cdelt = [-0.000277, 0.000277]
wcs.wcs.crval = [10.0, -20.0]
wcs.wcs.ctype = ["RA---TAN", "DEC--TAN"]
print(float(norm(data)[50, 50]), wcs.pixel_to_world(50, 50))
PY
```

### Required inputs
- Analysis target: image cube, table output, or WCS-projected figure.
- Output contract: file format (`.fits`, table, plot) and units expected by downstream steps.
- Coordinate metadata: reference frame/projection and pixel scale if WCS is involved.

### Validation checkpoints
- Confirm normalization output is finite and in expected range before plotting.
- Verify at least one pixel<->world round trip is numerically stable.
- Assert units and axis labels match the published analysis/output requirement.

## Scope
- Handle questions about output formats, analysis, and post-processing.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/visualization/normalization.rst`
- `docs/visualization/wcsaxes/overlays.rst`
- `docs/visualization/wcsaxes/ticks_labels_grid.rst`
- `docs/io/fits/appendix/faq.rst`
- `docs/units/physical_types.rst`
- `docs/visualization/rgb.rst`
- `docs/visualization/matplotlib_integration.rst`
- `docs/visualization/wcsaxes/slicing_datacubes.rst`
- `docs/visualization/wcsaxes/initializing_axes.rst`
- `docs/visualization/wcsaxes/controlling_axes.rst`
- `docs/wcs/wcstools.rst`
- `docs/visualization/wcsaxes/overlaying_coordinate_systems.rst`

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
- `astropy/visualization/mpl_normalize.py`
- `astropy/visualization/interval.py`
- `astropy/visualization/stretch.py`
- `astropy/wcs/utils.py`
- `astropy/wcs/wcs.py`
- `astropy/io/fits/hdu/image.py`
- `astropy/visualization/wcsaxes/transforms.py`
- `astropy/visualization/wcsaxes/ticks.py`
- `astropy/visualization/wcsaxes/grid_paths.py`
- `astropy/visualization/wcsaxes/coordinate_range.py`
- `astropy/visualization/wcsaxes/coordinate_helpers.py`
- `astropy/visualization/wcsaxes/coordinates_map.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" astropy cextern`).
