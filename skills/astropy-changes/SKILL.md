---
name: astropy-changes
description: This skill should be used when users ask about changes in astropy; it prioritizes documentation references and then source inspection only for unresolved details.
---

# astropy: Changes

## High-Signal Playbook

### Route conditions
- Use this skill for unreleased change fragments in `docs/changes/` and release-note fragment authoring/review.
- Route released user-facing summaries to `astropy-whatsnew`.
- Route deep behavior questions to the relevant subsystem skill after identifying the fragment.

### Triage questions
- What PR number is associated with the change?
- Which type applies: `feature`, `api`, `bugfix`, `perf`, or `other`?
- Is the change package-wide or subpackage-specific?
- Does one change require multiple fragments of different types?
- Is the fragment text full-sentence and code-marked with double backticks?
- Do we need a draft preview (`towncrier`) before merge?

### Canonical workflow
1. Choose filename pattern `<PR>.<TYPE>.rst` (`docs/changes/README.rst`).
2. If scoped to a subpackage, place it in the subdirectory; avoid `other` there.
3. Write concise, full-sentence ReST with double-backticked symbols.
4. Split into multiple files if both API and behavior changes are present.
5. Preview changelog rendering with `towncrier --draft --version <target>` when needed.
6. Cross-check fragment against modified source files.

### Minimal working example
```rst
# docs/changes/table/19321.bugfix.rst
Table join now preserves masked ``Quantity`` metadata when combining
columns with compatible units.
```

### Pitfalls and fixes
- Wrong filename schema breaks collection: enforce `<PR>.<TYPE>.rst` (`docs/changes/README.rst`).
- Using `other` in subpackage directories is disallowed.
- Fragment text as sentence fragment/no punctuation: rewrite as full sentence.
- Missing double backticks for symbols/options reduces clarity and formatting quality.
- Mis-typed category (`feature` vs `api`): split or ask for maintainer guidance.
- Skipping preview can hide malformed grouping in final notes (`docs/changes/template.rst`).

### Convergence and validation checks
- Filename, directory, and type all match policy.
- Fragment renders in expected section in `towncrier --draft` output.
- Fragment statement is traceable to changed source files.
- No duplicate or contradictory fragments for the same PR scope.

## Scope
- Handle questions about documentation grouped under the 'changes' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/changes/README.rst`
- `docs/changes/template.rst`
- `docs/changes/19050.other.rst`
- `docs/changes/18986.other.rst`
- `docs/changes/18962.other.rst`
- `docs/changes/utils/19142.bugfix.rst`
- `docs/changes/units/19055.bugfix.rst`
- `docs/changes/table/19199.bugfix.rst`
- `docs/changes/table/19173.feature.rst`
- `docs/changes/table/19123.feature.rst`
- `docs/changes/samp/19231.bugfix.rst`
- `docs/changes/nddata/18862.feature.rst`

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
- `astropy/units/utils.py`
- `astropy/units/typing_utils.py`
- `astropy/table/_np_utils.pyx`
- `astropy/samp/utils.py`
- `astropy/nddata/utils.py`
- `astropy/cosmology/_src/utils.py`
- `astropy/cosmology/_src/units.py`
- `astropy/cosmology/_src/units_equivalencies.py`
- `astropy/cosmology/_src/io/builtin/utils.py`
- `astropy/cosmology/_src/io/builtin/table.py`
- `astropy/coordinates/angles/utils.py`
- `astropy/coordinates/builtin_frames/utils.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" astropy cextern`).
