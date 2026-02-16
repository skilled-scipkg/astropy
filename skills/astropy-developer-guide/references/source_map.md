# astropy source map: Developer Guide

Generated from source roots:
- `astropy`
- `cextern`

Use this map only after exhausting the topic docs in `doc_map.md`.

## Topic query tokens
- `architecture`
- `contributing`
- `contribution`
- `develop`
- `developer`
- `development`
- `git`
- `internals`
- `maintainers`
- `plugin`
- `releasing`
- `resources`

## Fast source navigation
- `rg -n "<symbol_or_keyword>" astropy cextern`
- `rg -n "class|def|struct|namespace" astropy cextern`
- If a doc mentions a function/class, search that exact symbol first, then inspect nearby implementation files.

## Suggested source entry points
- `astropy/tests/runner.py` | score: 10 | matched tokens: development, maintainer, workflow
- `astropy/tests/helper.py` | score: 9 | matched tokens: development, contributing
- `astropy/conftest.py` | score: 8 | matched tokens: development
- `astropy/io/registry/core.py` | score: 8 | matched tokens: plugin, architecture
- `astropy/table/connect.py` | score: 8 | matched tokens: plugin, contribution
- `astropy/utils/introspection.py` | score: 7 | matched tokens: internals, architecture
- `astropy/utils/state.py` | score: 7 | matched tokens: internals
- `astropy/version.py` | score: 7 | matched tokens: releasing
- `astropy/logger.py` | score: 6 | matched tokens: resources
- `astropy/__init__.py` | score: 6 | matched tokens: architecture
