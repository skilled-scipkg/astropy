---
name: astropy-inputs-and-modeling
description: This skill should be used when users ask about inputs and modeling in astropy; it prioritizes documentation references and then source inspection only for unresolved details.
---

# astropy: Inputs and Modeling

## High-Signal Playbook

### Route conditions
- Use this skill for model setup, fitter behavior, periodogram modeling, structured units, cosmology I/O mappings, and cloud-hosted FITS inputs.
- Route generic API edge behavior to `astropy-api-and-scripting`.
- Route runtime orchestration/checkpointing to `astropy-simulation-workflows`.
- Route heavy parallel scaling concerns to `astropy-parallel-hpc`.

### Triage questions
- What model family is needed (analytic model, physical model, periodogram, cosmology format conversion)?
- Are parameters and inputs unit-bearing, and do equivalencies matter?
- Is fitting single-dataset, joint, or multiband?
- Which constraints are required (bounds/fixed/tied) and does the fitter support them?
- Is input data local or cloud-hosted FITS with selective reads?
- What acceptance metric defines success (residuals, power peak, parameter uncertainties)?

### Canonical workflow
1. Normalize inputs to explicit `Quantity`/table structures with units.
2. Pick a model and set parameter units up-front (`docs/modeling/units.rst`, `docs/modeling/add-units.rst`).
3. Use built-in fitters first; introduce custom fitter/statistic only if necessary (`docs/modeling/new-fitter.rst`).
4. For periodic signals, start with heuristic grids via `autopower` then refine (`docs/timeseries/lombscargle.rst`, `docs/timeseries/lombscarglemb.rst`).
5. For shared-parameter fits, verify `JointFitter` applicability before wiring constraints (`docs/modeling/jointfitter.rst`).
6. For remote FITS, combine `use_fsspec=True` with `.section` slicing (`docs/io/fits/usage/cloud.rst`).
7. Validate units, residuals, and stability against grid/initialization perturbations.

### Minimal working example
```python
import numpy as np
from astropy.timeseries import LombScargle
from astropy import units as u
from astropy.modeling.models import Gaussian1D

rng = np.random.default_rng(42)
t = 100 * rng.random(100)
y = np.sin(2 * np.pi * t) + 0.1 * rng.standard_normal(100)
freq, power = LombScargle(t, y).autopower(minimum_frequency=0.1, maximum_frequency=1.9)
print(freq[np.argmax(power)])

g = Gaussian1D(mean=3 * u.m, stddev=5 * u.cm)
print(g(2.9 * u.m))
```

### Pitfalls and fixes
- Unit-enabled custom models without `input_units`/`_parameter_units_for_data_units` lead to opaque unit errors (`docs/modeling/add-units.rst`).
- Once a parameter is initialized with units, assigning a bare scalar is ambiguous and fails (`docs/modeling/units.rst`).
- Equivalencies should be applied at evaluation time, not baked into model parameters (`docs/modeling/units.rst`).
- Sparse/coarse frequency grids can hide strong periodic signals: rely on heuristic `autopower` then tune (`docs/timeseries/lombscargle.rst`).
- `JointFitter` does not support fixed/bounded/tied constraints (`docs/modeling/jointfitter.rst`).
- Remote FITS cutouts are efficient with `.section`; `.data` or external compression can trigger full downloads (`docs/io/fits/usage/cloud.rst`).

### Convergence and validation checks
- Confirm fitted parameter units are physically consistent and expected.
- Re-run fit with perturbed initial guesses; require stable solution neighborhood.
- Check residual structure or periodogram peak stability under modest grid refinement.
- For remote FITS pipelines, verify subset reads and avoid accidental full-file pulls.
- If doc behavior and runtime diverge, inspect source entry points below.

## Scope
- Handle questions about inputs, system setup, models, and physical parameterization.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/modeling/add-units.rst`
- `docs/modeling/new-fitter.rst`
- `docs/timeseries/lombscarglemb.rst`
- `docs/timeseries/lombscargle.rst`
- `docs/table/construct_table.rst`
- `docs/modeling/jointfitter.rst`
- `docs/table/table_and_dataframes.rst`
- `docs/modeling/units.rst`
- `docs/cosmology/io/builtin.rst`
- `docs/io/fits/usage/cloud.rst`
- `docs/units/structured_units.rst`
- `docs/modeling/physical_models.rst`

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
- `astropy/modeling/fitting.py`
- `astropy/modeling/functional_models.py`
- `astropy/modeling/physical_models.py`
- `astropy/modeling/_fitting_parallel.py`
- `astropy/timeseries/periodograms/lombscargle/core.py`
- `astropy/timeseries/periodograms/lombscargle/implementations/main.py`
- `astropy/timeseries/periodograms/lombscargle_multiband/core.py`
- `astropy/cosmology/_src/io/builtin/model.py`
- `astropy/cosmology/_src/io/builtin/table.py`
- `astropy/units/structured.py`
- `astropy/table/_dataframes.py`
- `astropy/io/fits/hdu/table.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" astropy cextern`).
