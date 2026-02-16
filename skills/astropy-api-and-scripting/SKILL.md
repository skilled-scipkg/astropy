---
name: astropy-api-and-scripting
description: This skill should be used when users ask about api and scripting in astropy; it prioritizes documentation references and then source inspection only for unresolved details.
---

# astropy: API and Scripting

## High-Signal Playbook

### Route conditions
- Use this skill for API behavior in `Quantity`, masked arrays, SAMP messaging, and FITS/table programmatic interfaces.
- Route data-model construction/fitting strategy to `astropy-inputs-and-modeling`.
- Route file-format specific workflows to `astropy-io`.
- Route release-specific regressions to `astropy-whatsnew`/`astropy-changes`.

### Triage questions
- Which API surface is involved (`units`, `masked`, `samp`, `io.fits`, mixins)?
- Must units/masks survive every operation?
- Are third-party arrays/dataframes involved (`numpy`, `pandas`, `scipy`)?
- Is this interactive scripting, library code, or plugin/extension code?
- Are warnings/errors currently seen, and are they reproducible in a tiny snippet?
- Are remote clients/hubs required (SAMP hub running)?

### Canonical workflow
1. Start from the primary API docs for the subsystem (`docs/utils/masked/index.rst`, `docs/units/quantity.rst`, `docs/samp/index.rst`, `docs/io/fits/api/index.rst`).
2. Build a minimal reproducer with explicit units/masks and no external dependencies.
3. Cross-check known caveats before changing code (`docs/known_issues.rst`).
4. Choose the stable API pattern (e.g., explicit `Quantity(...)`, `Masked`, unified table I/O).
5. Re-run with warnings visible and assert output types/units.
6. If behavior is still unclear, inspect the corresponding helper modules in source.

### Minimal working example
```python
import numpy as np
from astropy import units as u
from astropy.utils.masked import Masked

mq = Masked([1.0, 2.0, 3.0], mask=[False, False, True]) * u.m
result = mq + 25 * u.cm
print(result.filled(fill_value=-75 * u.cm))

nu = (1000 * u.nm).to(u.Hz, equivalencies=u.spectral())
print(nu)
```

### Pitfalls and fixes
- `np.prod` is unsupported for `Quantity`: use explicit math that preserves units (`docs/known_issues.rst`).
- `pandas.Series * unit` does not reliably produce `Quantity`: use `u.Quantity(series, unit)` (`docs/known_issues.rst`).
- `np.broadcast_to` and similar can drop units unless `subok=True` (`docs/known_issues.rst`).
- `Masked` reductions propagate masks (unlike `numpy.ma` defaults): use the documented helpers when skip behavior is intended (`docs/utils/masked/index.rst`).
- Setting `.mask` on slices may not propagate as expected: mask elements explicitly (`docs/utils/masked/index.rst`).
- SAMP calls require a running hub: launch/connect hub before client calls (`docs/samp/index.rst`).

### Convergence and validation checks
- Assert output object classes (`Quantity`, `MaskedQuantity`, `Table` or `QTable`) after each key step.
- Assert units are preserved or intentionally converted with `.to(...)`.
- Treat warnings in known-issues paths as gates, not noise.
- For unresolved behavior, trace helper functions in source entry points below.

## Scope
- Handle questions about language bindings, APIs, and programmatic interfaces.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/utils/masked/index.rst`
- `docs/samp/index.rst`
- `docs/index.rst`
- `docs/nddata/mixins/index.rst`
- `docs/io/fits/api/index.rst`
- `docs/known_issues.rst`
- `docs/coordinates/spectralcoord.rst`
- `docs/units/quantity.rst`
- `docs/nddata/subclassing.rst`
- `docs/io/unified_table_fits.rst`
- `docs/development/style-guide.rst`
- `docs/cosmology/dev.rst`

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
- `astropy/utils/masked/function_helpers.py`
- `astropy/utils/masked/core.py`
- `astropy/units/quantity.py`
- `astropy/units/quantity_helper/function_helpers.py`
- `astropy/units/quantity_helper/helpers.py`
- `astropy/units/function/logarithmic.py`
- `astropy/units/function/core.py`
- `astropy/samp/utils.py`
- `astropy/nddata/mixins/ndio.py`
- `astropy/table/mixins/__init__.py`
- `astropy/io/fits/hdu/table.py`
- `astropy/cosmology/units.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" astropy cextern`).
