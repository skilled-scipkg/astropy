---
name: astropy-whatsnew
description: This skill should be used when users ask about whatsnew in astropy; it prioritizes documentation references and then source inspection only for unresolved details.
---

# astropy: Whatsnew

## High-Signal Playbook

### Route conditions
- Use this skill for released-version change summaries, upgrade impact checks, and "is this feature available in version X?" questions.
- Route unreleased PR fragment inspection/authoring to `astropy-changes`.
- Route package-specific usage details to the relevant functional skill after identifying the release boundary.

### Triage questions
- What exact installed version is being used right now?
- Which target version is being compared against?
- Which subpackage behavior is in question?
- Is the user asking about new feature, deprecation, regression, or migration risk?
- Is a release-note citation required for decision records?
- Do we need to map notes to concrete source modules for follow-up?

### Canonical workflow
1. Read installed version at runtime (`astropy.__version__`).
2. Use `docs/whatsnew/index.rst` to map to the correct release page.
3. Check both current and target release notes for the relevant subsystem.
4. Extract concrete action items (API rename, behavior change, dependency constraints).
5. If release notes are high level, inspect module `__init__`/version files for confirmation.
6. For unreleased behavior, pivot to `docs/changes/*` via `astropy-changes`.

### Minimal working example
```python
import astropy

major_minor = ".".join(astropy.__version__.split(".")[:2])
print("Installed:", astropy.__version__)
print(f"Release notes: https://docs.astropy.org/en/v{major_minor}.x/whatsnew/{major_minor}.html")
```

### Pitfalls and fixes
- "What's New" examples are frozen in time; for current API use main docs after identifying release (`docs/whatsnew/index.rst`).
- Local per-release files such as `docs/whatsnew/7.2.rst` are pointer pages, not full narratives.
- Confusing released notes with unreleased fragments: use `docs/changes/` for pending changes.
- Version mismatch in editable/dev installs: always print runtime version before citing notes.
- Subpackage details may require drilling into module-level source after release-note triage.

### Convergence and validation checks
- Confirm runtime version and cited release-note URL align.
- Verify the claimed behavior appears in the specific release window.
- If no match in released notes, check `astropy-changes` before concluding regression.
- Smoke-test the impacted subpackage after upgrade decision.

## Scope
- Handle questions about documentation grouped under the 'whatsnew' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/whatsnew/index.rst`
- `docs/whatsnew/7.2.rst`
- `docs/whatsnew/7.1.rst`
- `docs/whatsnew/7.0.rst`
- `docs/whatsnew/6.1.rst`
- `docs/whatsnew/6.0.rst`
- `docs/whatsnew/5.3.rst`
- `docs/whatsnew/5.2.rst`
- `docs/whatsnew/5.1.rst`
- `docs/whatsnew/5.0.rst`
- `docs/whatsnew/4.3.rst`
- `docs/whatsnew/4.2.rst`

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
- `astropy/version.py`
- `astropy/__init__.py`
- `astropy/utils/introspection.py`
- `astropy/tests/runner.py`
- `astropy/units/quantity.py`
- `astropy/table/table.py`
- `astropy/time/core.py`
- `astropy/coordinates/sky_coordinate.py`
- `astropy/io/fits/hdu/table.py`
- `astropy/wcs/wcs.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" astropy cextern`).
