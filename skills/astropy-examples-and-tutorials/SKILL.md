---
name: astropy-examples-and-tutorials
description: This skill should be used when users ask about examples and tutorials in astropy; it prioritizes documentation references and then source inspection only for unresolved details.
---

# astropy: Examples and Tutorials

## High-Signal Playbook

### Route conditions
- Use this skill when the user asks "show me how" for periodograms, table ops, unit conversions, or coordinate usage patterns.
- Route production modeling choices to `astropy-inputs-and-modeling`.
- Route file-format specifics and large I/O workflows to `astropy-io`.
- Route API edge behavior to `astropy-api-and-scripting`.

### Triage questions
- Which example family is closest: timeseries, table, units, or coordinates?
- Is synthetic data acceptable, or must the example use external/package data?
- Are uncertainties available and required in the example?
- Is the deliverable a plot, derived period, transformed coordinates, or table artifact?
- What constraints matter most: readability, speed, or numerical robustness?
- Do we need an immediately runnable snippet or a template to adapt?

### Canonical workflow
1. Pick the closest tutorial page in this skill's primary docs.
2. Start from the smallest example in that page, not the full tutorial.
3. Keep unit-bearing data as `Quantity`/`QTable` from the beginning.
4. Validate baseline output before altering grid size, objective, or formats.
5. Adapt one parameter family at a time (frequency grid, grouping keys, frame/representation).
6. If behavior diverges, inspect corresponding implementation files from `references/source_map.md`.

### Minimal working example
```python
import numpy as np
import astropy.units as u
from astropy.timeseries import BoxLeastSquares

rng = np.random.default_rng(42)
t = rng.uniform(0, 20, 2000)
y = np.ones_like(t) - 0.1 * ((t % 3) < 0.2) + 0.01 * rng.standard_normal(len(t))

bls = BoxLeastSquares(t * u.day, y, dy=0.01)
periodogram = bls.autopower(0.2)
best = np.argmax(periodogram.power)
print(periodogram.period[best], periodogram.power[best])
```

### Pitfalls and fixes
- Coarse period/frequency grids can hide true peaks: prefer `autopower` heuristics first (`docs/timeseries/lombscargle.rst`, `docs/timeseries/bls.rst`).
- `vstack` does not sort or deduplicate time series: sort explicitly after stacking (`docs/timeseries/analysis.rst`).
- Table metadata merges can warn or conflict: choose explicit merge strategy (`docs/table/operations.rst`).
- Unit string formatting/parsing may warn for non-standard units: set strictness intentionally (`docs/units/format.rst`).
- DataFrame conversions are convenient but can drop astronomy-specific semantics: confirm unit/time/metadata fidelity (`docs/table/dataframes.rst`).

### Convergence and validation checks
- Confirm recovered period/frequency is stable when grid settings are moderately tightened.
- Assert expected output units (`period`, `frequency`, transformed quantities).
- For table operations, validate row count/order and metadata handling.
- Keep one unchanged baseline example output as regression reference while adapting.

## Scope
- Handle questions about worked examples, tutorials, and cookbook usage.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/units/format.rst`
- `docs/timeseries/bls.rst`
- `docs/timeseries/analysis.rst`
- `docs/units/equivalencies.rst`
- `docs/table/operations.rst`
- `docs/table/mixin_columns.rst`
- `docs/table/dataframes.rst`
- `docs/io/unified_table.rst`
- `docs/coordinates/velocities.rst`
- `docs/coordinates/representations.rst`
- `docs/coordinates/frames.rst`
- `docs/coordinates/angles.rst`

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
- `astropy/timeseries/periodograms/bls/core.py`
- `astropy/timeseries/periodograms/bls/methods.py`
- `astropy/timeseries/periodograms/bls/_impl.pyx`
- `astropy/timeseries/periodograms/lombscargle/implementations/fast_impl.py`
- `astropy/table/operations.py`
- `astropy/table/_dataframes.py`
- `astropy/units/equivalencies.py`
- `astropy/units/format/fits.py`
- `astropy/coordinates/angles/formats.py`
- `astropy/coordinates/angles/core.py`
- `astropy/coordinates/builtin_frames/__init__.py`
- `astropy/io/fits/hdu/table.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" astropy cextern`).
