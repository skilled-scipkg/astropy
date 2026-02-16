# Evidence: astropy-getting-started

## Primary docs
- `docs/units/index.rst`
- `docs/uncertainty/index.rst`
- `docs/timeseries/index.rst`
- `docs/stats/index.rst`
- `docs/modeling/index.rst`
- `docs/wcs/index.rst`
- `docs/time/index.rst`
- `docs/table/index.rst`
- `docs/nddata/index.rst`
- `docs/development/quickstart.rst`
- `docs/cosmology/index.rst`
- `docs/coordinates/index.rst`

## Primary source entry points
- `skills/astropy-getting-started/references/doc_map.md`
- `astropy/visualization/wcsaxes/utils.py`
- `astropy/visualization/wcsaxes/coordinates_map.py`
- `astropy/timeseries/periodograms/lombscargle/utils.py`
- `astropy/timeseries/periodograms/lombscargle/implementations/utils.py`
- `astropy/wcs/utils.py`
- `astropy/visualization/units.py`
- `astropy/visualization/time.py`
- `astropy/units/utils.py`
- `astropy/units/typing_utils.py`
- `astropy/time/utils.py`
- `astropy/table/_np_utils.pyx`
- `astropy/nddata/utils.py`
- `astropy/modeling/utils.py`
- `astropy/cosmology/units.py`
- `astropy/constants/utils.py`
- `astropy/constants/config.py`
- `astropy/wcs/wcsapi/utils.py`
- `astropy/units/format/fits.py`
- `astropy/io/votable/table.py`

## Extracted headings
- define a model for a line
- generate x, y data non-uniformly spaced in x
- add noise to y measurements
- initialize a linear fitter
- initialize a linear model
- fit the data with the fitter
- plot the model

## Executable command hints
- Python parser if needed.  Note that the configuration value is a string, not a

## Warnings and pitfalls
- operations where error analysis becomes untenable, |Distribution| still powers
- proper care is taken with sampling error.
- An important note of warning, however, is that the covariance is only preserved
