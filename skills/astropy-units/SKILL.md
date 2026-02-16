---
name: astropy-units
description: This skill should be used when users ask about units in astropy; it prioritizes documentation references and then source inspection only for unresolved details.
---

# astropy: Units

## High-Signal Playbook

### Quick-start command
```bash
python - <<'PY'
from astropy import units as u

lam = 500 * u.nm
nu = lam.to(u.THz, equivalencies=u.spectral())
speed = (120 * u.km / u.h).to(u.m / u.s)
print(nu, speed)
PY
```

### Required inputs
- Source values and required destination units.
- Any needed equivalencies (spectral, temperature-energy, brightness, etc.).
- Tolerance policy for round-trip conversions and formatted output.

### Validation checkpoints
- Verify conversions preserve physical type and expected dimensionality.
- Run at least one round-trip conversion and compare against tolerance.
- Confirm unit formatting/parsing behavior is explicit for serialization paths.

## Scope
- Handle questions about documentation grouped under the 'units' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/units/standard_units.rst`
- `docs/units/type_hints.rst`

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
- `astropy/units/core.py`
- `astropy/units/quantity.py`
- `astropy/units/equivalencies.py`
- `astropy/units/structured.py`
- `astropy/units/format/generic.py`
- `astropy/units/function/core.py`
- `astropy/units/quantity_helper/function_helpers.py`
- `astropy/visualization/units.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" astropy cextern`).
