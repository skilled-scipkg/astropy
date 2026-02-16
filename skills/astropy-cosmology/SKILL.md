---
name: astropy-cosmology
description: This skill should be used when users ask about cosmology in astropy; it prioritizes documentation references and then source inspection only for unresolved details.
---

# astropy: Cosmology

## High-Signal Playbook

### Quick-start command
```bash
python - <<'PY'
import astropy.units as u
from astropy.cosmology import Planck18

z = 1.5
d_l = Planck18.luminosity_distance(z).to(u.Gpc)
age = Planck18.age(z).to(u.Gyr)
print(d_l, age)
PY
```

### Required inputs
- Cosmology model choice (`Planck18`, custom FLRW, or serialized model file).
- Redshift/range and expected observables (distance, age, volume, etc.).
- Unit conventions and serialization target when exporting/importing models.

### Validation checkpoints
- Confirm model parameters and units before evaluation.
- Verify key outputs are monotonic/physically plausible across sampled redshift.
- Round-trip one model through I/O and compare key parameters for equality.

## Scope
- Handle questions about documentation grouped under the 'cosmology' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/cosmology/realizations.rst`
- `docs/cosmology/io/custom.rst`

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
- `astropy/cosmology/realizations.py`
- `astropy/cosmology/_src/flrw/base.py`
- `astropy/cosmology/_src/flrw/lambdacdm.py`
- `astropy/cosmology/_src/parameter/core.py`
- `astropy/cosmology/_src/io/builtin/model.py`
- `astropy/cosmology/_src/io/builtin/table.py`
- `astropy/cosmology/_src/funcs/optimize.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" astropy cextern`).
