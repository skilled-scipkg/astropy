---
name: astropy-parallel-hpc
description: This skill should be used when users ask about parallel and hpc in astropy; it prioritizes documentation references and then source inspection only for unresolved details.
---

# astropy: Parallel and HPC

## High-Signal Playbook

### Quick-start command
```bash
python - <<'PY'
import numpy as np
import astropy.units as u
from astropy.coordinates import SkyCoord

n = 200000
ra = np.linspace(0, 359.9, n) * u.deg
dec = np.linspace(-80, 80, n) * u.deg
c = SkyCoord(ra=ra, dec=dec, frame="icrs")
g = c.galactic
print(g.l.shape, g.b.unit)
PY
```

### Required inputs
- Array/cube sizes and memory budget for the target machine.
- Throughput goal (latency per batch, total runtime, or nightly budget).
- Parallel execution constraints (thread caps, scheduler limits, and I/O bandwidth).

### Validation checkpoints
- Confirm vectorized operations are used before considering process-level parallelism.
- Benchmark one realistic batch size and track wall time + peak memory.
- Verify numerical outputs remain unchanged when tuning thread/process settings.

## Scope
- Handle questions about MPI/OpenMP/GPU execution, scaling, and batch systems.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/table/indexing.rst`
- `docs/coordinates/performance.inc.rst`
- `docs/io/fits/api/images.rst`
- `docs/time/performance.inc.rst`
- `docs/table/performance.inc.rst`
- `docs/units/performance.inc.rst`
- `docs/stats/performance.inc.rst`
- `docs/nddata/performance.inc.rst`
- `docs/convolution/performance.inc.rst`
- `docs/io/ascii/performance.inc.rst`
- `docs/wcs/performance.inc.rst`
- `docs/visualization/performance.inc.rst`

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
- `astropy/table/operations.py`
- `astropy/table/groups.py`
- `astropy/io/fits/file.py`
- `astropy/time/core.py`
- `astropy/units/quantity.py`
- `astropy/convolution/convolve.py`
- `astropy/io/fits/hdu/table.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" astropy cextern`).
