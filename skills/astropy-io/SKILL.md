---
name: astropy-io
description: This skill should be used when users ask about io in astropy; it prioritizes documentation references and then source inspection only for unresolved details.
---

# astropy: Io

## High-Signal Playbook

### Quick-start command
```bash
python - <<'PY'
from astropy import units as u
from astropy.table import QTable

t = QTable({"id": [1, 2], "flux": [1.2, 3.4] * u.Jy})
t.write("/tmp/astropy_io_check.ecsv", overwrite=True)
t2 = QTable.read("/tmp/astropy_io_check.ecsv")
print(t2.colnames, t2["flux"].unit, len(t2))
PY
```

### Required inputs
- Concrete input/output formats and sample payloads.
- Unit and metadata preservation requirements across I/O boundaries.
- Local/remote storage constraints (streaming, cloud URLs, partial reads).

### Validation checkpoints
- Round-trip one representative dataset through target format(s).
- Confirm key units, masks, and metadata survive read/write.
- Check row/column counts and key identifiers after conversion.

## Scope
- Handle questions about documentation grouped under the 'io' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/io/unified_table_text.rst`
- `docs/io/votable/table_element.rst`
- `docs/io/ascii/ecsv.rst`
- `docs/io/ascii/fixed_width_gallery.rst`
- `docs/io/unified_image.rst`
- `docs/io/fits/usage/scripts.rst`
- `docs/io/unified.rst`
- `docs/io/votable/coosys_element.rst`
- `docs/io/votable/references.txt`
- `docs/io/ascii/toc.txt`
- `docs/io/ascii/references.txt`

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
- `astropy/io/registry/core.py`
- `astropy/io/ascii/core.py`
- `astropy/io/votable/table.py`
- `astropy/io/ascii/ecsv.py`
- `astropy/io/fits/connect.py`
- `astropy/io/fits/hdu/table.py`
- `astropy/table/connect.py`
- `astropy/table/table.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" astropy cextern`).
