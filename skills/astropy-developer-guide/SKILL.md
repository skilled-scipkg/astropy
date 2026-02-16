---
name: astropy-developer-guide
description: This skill should be used when users ask about developer guide in astropy; it prioritizes documentation references and then source inspection only for unresolved details.
---

# astropy: Developer Guide

## High-Signal Playbook

### Quick-start command
```bash
python -m pytest -q astropy/tests/tests/test_runner.py
python -m pytest -q astropy/table/tests/test_operations.py -k join
```

### Required inputs
- Target subsystem/module and expected behavior change.
- Minimal reproducer or failing test path.
- Branch state (base commit, local edits, and intended release target).

### Validation checkpoints
- Reproduce the issue with a focused test before changing code.
- Keep one narrow regression test that fails before and passes after the fix.
- Run impacted subsystem tests and verify no unrelated failures were introduced.

## Scope
- Handle questions about developer architecture, extension points, and contribution workflow.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/development/maintainers/index.rst`
- `docs/development/git_resources.rst`
- `docs/development/maintainers/releasing.rst`

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
- `astropy/tests/runner.py`
- `astropy/tests/helper.py`
- `astropy/conftest.py`
- `astropy/io/registry/core.py`
- `astropy/table/connect.py`
- `astropy/utils/introspection.py`
- `astropy/utils/state.py`
- `astropy/version.py`
- `astropy/logger.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" astropy cextern`).
