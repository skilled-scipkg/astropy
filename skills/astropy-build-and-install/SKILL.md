---
name: astropy-build-and-install
description: This skill should be used when users ask about build and install in astropy; it prioritizes documentation references and then source inspection only for unresolved details.
---

# astropy: Build and Install

## High-Signal Playbook

### Quick-start command
```bash
python -m pip install -e . --no-build-isolation
python - <<'PY'
import astropy
from astropy.wcs import WCS
print("astropy:", astropy.__version__)
print("wcs-ok:", WCS is not None)
PY
python -m pytest -q astropy/tests/tests/test_runner.py
```

### Required inputs
- Python version and environment manager (`venv`, `conda`, or system Python).
- Compiler toolchain availability for extension builds.
- Target validation scope: import smoke only, or selected test module(s).

### Validation checkpoints
- Editable install completes without build backend failures.
- `import astropy` and a compiled-extension import (`astropy.wcs`) succeed.
- At least one targeted test module runs cleanly in the active environment.

## Scope
- Handle questions about build, installation, compilation, and environment setup.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/convolution/index.rst`
- `docs/development/testguide.rst`
- `docs/development/development_details.rst`
- `docs/development/codeguide.rst`
- `docs/development/vision.rst`
- `docs/development/ccython.rst`

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
- `pyproject.toml`
- `setup.py`
- `cextern/wcslib/configure.ac`
- `astropy/wcs/setup_package.py`
- `astropy/io/fits/hdu/compressed/setup_package.py`
- `astropy/table/setup_package.py`
- `astropy/time/setup_package.py`
- `astropy/convolution/setup_package.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" astropy cextern`).
