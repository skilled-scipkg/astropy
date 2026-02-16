---
name: astropy-timeseries
description: This skill should be used when users ask about timeseries in astropy; it prioritizes documentation references and then source inspection only for unresolved details.
---

# astropy: Timeseries

## High-Signal Playbook

### Quick-start command
```bash
python - <<'PY'
import numpy as np
from astropy.timeseries import LombScargle, TimeSeries
from astropy.time import Time

t = Time(59000.0 + 0.1 * np.arange(300), format="mjd")
flux = np.sin(2 * np.pi * 0.35 * 0.1 * np.arange(300))
ts = TimeSeries(time=t, data={"flux": flux})
freq, power = LombScargle(ts.time.mjd, ts["flux"]).autopower(minimum_frequency=0.1, maximum_frequency=1.0)
print(float(freq[np.argmax(power)]))
PY
```

### Required inputs
- Sampling cadence and time scale/format.
- Signal/noise assumptions and target frequency window.
- Expected output artifact (periodogram, binned series, or downsampled table).

### Validation checkpoints
- Confirm time axis uses explicit format/scale with monotonic ordering.
- Validate recovered peak frequency against synthetic truth in a smoke run.
- Verify downsampling/binning preserves expected units and metadata.

## Scope
- Handle questions about documentation grouped under the 'timeseries' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `docs/timeseries/initializing.rst`
- `docs/timeseries/data_access.rst`

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
- `astropy/timeseries/core.py`
- `astropy/timeseries/sampled.py`
- `astropy/timeseries/downsample.py`
- `astropy/timeseries/binned.py`
- `astropy/timeseries/periodograms/base.py`
- `astropy/timeseries/periodograms/lombscargle/core.py`
- `astropy/timeseries/periodograms/lombscargle/implementations/main.py`
- `astropy/timeseries/periodograms/bls/core.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" astropy cextern`).
