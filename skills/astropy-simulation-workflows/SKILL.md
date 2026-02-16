---
name: astropy-simulation-workflows
description: This skill should be used when users ask about simulation workflows in astropy; it prioritizes documentation references and then source inspection only for unresolved details.
---

# astropy: Simulation Workflows

## High-Signal Playbook

### Quick-start command
```bash
python - <<'PY'
import numpy as np
import astropy.units as u
from astropy.timeseries import LombScargle

rng = np.random.default_rng(42)
t = np.linspace(0, 30, 500) * u.day
true_f = 0.42 / u.day
y = np.sin((2 * np.pi * true_f * t).decompose().value) + 0.05 * rng.standard_normal(t.size)
freq, power = LombScargle(t, y).autopower(minimum_frequency=0.1 / u.day, maximum_frequency=1.0 / u.day)
best_f = freq[np.argmax(power)]
print(best_f.to(1 / u.day), float(abs((best_f - true_f) / true_f)))
PY
```

### Required inputs
- Simulation objective and measurable success criterion.
- Time/cadence grid, noise model, and random seed policy.
- Runtime constraints: maximum wall time, memory, and checkpoint cadence.

### Validation checkpoints
- Recover known synthetic parameters within tolerance before using real data.
- Re-run with at least one perturbed seed/grid and confirm stable conclusions.
- Persist minimal artifacts (config, seed, summary metrics) for reproducibility.

## Scope
- Handle questions about simulation setup, execution flow, and runtime controls.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/development/git_edit_workflow_examples.rst`
- `docs/development/maintainers/maintainer_workflow.rst`
- `docs/development/maintainers/testhelpers.rst`

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
- `astropy/timeseries/periodograms/lombscargle/core.py`
- `astropy/timeseries/periodograms/lombscargle/implementations/main.py`
- `astropy/timeseries/core.py`
- `astropy/modeling/fitting.py`
- `astropy/time/core.py`
- `astropy/table/table.py`
- `astropy/tests/runner.py`
- `astropy/tests/helper.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" astropy cextern`).
