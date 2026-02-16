---
name: astropy-table
description: This skill should be used when users ask about table in astropy; it prioritizes documentation references and then source inspection only for unresolved details.
---

# astropy: Table

## High-Signal Playbook

### Quick-start command
```bash
python - <<'PY'
from astropy import units as u
from astropy.table import QTable, join

left = QTable({"id": [1, 2], "flux": [3.0, 4.5] * u.Jy})
right = QTable({"id": [1, 2], "snr": [10.0, 18.0]})
merged = join(left, right, keys="id")
print(merged.colnames, merged["flux"].unit, len(merged))
PY
```

### Required inputs
- Schema for key columns and join/group operations.
- Unit and mask expectations for each table column.
- Expected row cardinality/order constraints after operations.

### Validation checkpoints
- Assert row counts and key uniqueness before and after joins.
- Confirm units/masks persist through merge/group/filter steps.
- Compare one output table against a frozen baseline for regressions.

## Scope
- Handle questions about documentation grouped under the 'table' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/table/masking.rst`
- `docs/table/pandas.rst`
- `docs/table/implementation_details.rst`

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
- `astropy/table/table.py`
- `astropy/table/operations.py`
- `astropy/table/groups.py`
- `astropy/table/serialize.py`
- `astropy/table/pandas.py`
- `astropy/table/_dataframes.py`
- `astropy/table/connect.py`
- `astropy/table/table_helpers.py`
- `astropy/table/sorted_array.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" astropy cextern`).
