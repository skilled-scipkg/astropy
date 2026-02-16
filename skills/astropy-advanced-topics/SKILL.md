---
name: astropy-advanced-topics
description: This skill should be used when users ask about advanced and specialized topics in astropy; it prioritizes documentation references and then source inspection only for unresolved details.
---

# astropy: Advanced and Specialized Topics

## High-Signal Playbook

### Quick-start command
```bash
python - <<'PY'
import numpy as np
import astropy.units as u
from astropy.convolution import Box1DKernel, convolve
from astropy.stats import circmean

x = np.array([0.0, 1.0, 0.0, 0.0])
smoothed = convolve(x, Box1DKernel(3), normalize_kernel=False)
angles = [350, 10, 20] * u.deg
print(smoothed.tolist(), circmean(angles).to(u.deg))
PY
```

### Required inputs
- Narrow topic target (config, policy/meta docs, circ stats, NDData mixins, convolution behavior).
- Concrete artifact to validate (config path, computed statistic, transformed array).
- Tolerance/acceptance rule for the specific specialized behavior.

### Validation checkpoints
- Confirm the request remains narrow; route broader workflows to dedicated topic skills.
- Validate one reproducible numeric/output check before scaling complexity.
- If behavior contradicts docs, inspect targeted source entries below rather than broad repo scans.

## Route conditions
- Use this skill for narrow or policy-style topics that were collapsed from single-doc skills.
- Typical routes in this skill:
  - Project/meta docs: user-guide index, project details, impact/health, changelog, robots, credits, license, LTS policy.
  - Configuration/environment docs: astropy config defaults and environment variables.
  - Narrow technical docs: convolution non-normalized kernels, NDData I/O mixin, circular statistics.
  - Specialized coordinate docs: remote-method usage tips and common coordinate mistakes.
- If a request expands into a broader workflow, route out to the main topic skills (`astropy-io`, `astropy-coordinates`, `astropy-analysis-and-output`, `astropy-inputs-and-modeling`).

## Scope
- Handle questions about overflow specialized documentation not captured by higher-priority skills.
- Keep responses concise and doc-anchored; avoid broad function-by-function coverage.

## Primary documentation references
- `docs/index_project_details.rst`
- `docs/impact_health.rst`
- `docs/environment_variables.rst`
- `docs/changelog.rst`
- `docs/robots.txt`
- `docs/config/astropy_config.rst`
- `docs/index_user_docs.rst`
- `docs/license.rst`
- `docs/credits.rst`
- `docs/lts_policy.rst`
- `docs/glossary.rst`
- `docs/convolution/non_normalized_kernels.rst`
- `docs/nddata/mixins/ndio.rst`
- `docs/stats/circ.rst`
- `docs/coordinates/remote_methods.rst`
- `docs/coordinates/common_errors.rst`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the combined inventory.
- For behavior questions, open targeted source entry points from `references/source_map.md`.
- Keep citations as exact file paths.

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
- `astropy/config/configuration.py`
- `astropy/config/paths.py`
- `astropy/constants/config.py`
- `astropy/convolution/kernels.py`
- `astropy/convolution/convolve.py`
- `astropy/convolution/_convolve.pyx`
- `astropy/nddata/mixins/ndio.py`
- `astropy/nddata/mixins/ndarithmetic.py`
- `astropy/nddata/nddata_withmixins.py`
- `astropy/stats/circstats.py`
- `astropy/coordinates/errors.py`
- `astropy/coordinates/angles/errors.py`
- `astropy/coordinates/name_resolve.py`
- `astropy/utils/data.py`
- `astropy/__init__.py`
- `astropy/version.py`
- `cextern/wcslib/wcsconfig.h.in`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" astropy cextern`).
