# Evidence: astropy-inputs-and-modeling

## Primary docs
- `docs/modeling/add-units.rst`
- `docs/modeling/new-fitter.rst`
- `docs/timeseries/lombscarglemb.rst`
- `docs/timeseries/lombscargle.rst`
- `docs/table/construct_table.rst`
- `docs/modeling/jointfitter.rst`
- `docs/table/table_and_dataframes.rst`
- `docs/modeling/units.rst`
- `docs/cosmology/io/builtin.rst`
- `docs/io/fits/usage/cloud.rst`
- `docs/units/structured_units.rst`
- `docs/modeling/physical_models.rst`

## Primary source entry points
- `skills/astropy-inputs-and-modeling/references/doc_map.md`
- `astropy/modeling/physical_models.py`
- `astropy/cosmology/_src/io/builtin/model.py`
- `astropy/cosmology/_src/io/builtin/table.py`
- `astropy/units/structured.py`
- `astropy/modeling/models/__init__.py`
- `astropy/modeling/functional_models.py`
- `astropy/modeling/polynomial.py`
- `astropy/modeling/fitting.py`
- `astropy/modeling/_fitting_parallel.py`
- `astropy/timeseries/periodograms/lombscargle_multiband/__init__.py`
- `astropy/timeseries/periodograms/lombscargle/__init__.py`
- `astropy/timeseries/periodograms/lombscargle_multiband/implementations/__init__.py`
- `astropy/timeseries/periodograms/lombscargle/implementations/__init__.py`
- `astropy/cosmology/_src/io/builtin/__init__.py`
- `astropy/timeseries/periodograms/lombscargle_multiband/core.py`
- `astropy/timeseries/periodograms/lombscargle/core.py`
- `astropy/timeseries/periodograms/lombscargle_multiband/implementations/main.py`
- `astropy/timeseries/periodograms/lombscargle/implementations/main.py`
- `astropy/visualization/units.py`

## Extracted headings
- Most currently defined fitters take no arguments in their
- __init__, but the option certainly exists for custom fitters
- ...
- coefficients from a 5-term Fourier fit to SDSS object 1019544
- generate data and compute the periodogram
- compute the best-fit model
- set up the figure & axes for plotting
- plot the raw data
- plot the periodogram
- plot the false-alarm levels
- plot the phased data & model in the inset
- Here is my explanatory text. This is awesome.

## Executable command hints
- (none extracted)

## Warnings and pitfalls
- If the user then gives values with incorrect input units, a clear error will be
- package or write a user-defined fitter.  In short, one needs to define an error
- Next, the error function takes a list of parameters returned by an iteration of
- the data.  But this conclusion is in error: there is in fact a strong periodic
- periodic component, an important consideration is the significance of the
- In all of this, it is important to keep in mind a few caveats:
- There is a slightly subtle issue that is important to understand about the way
- However, caution must be exercised because the new table data and original data
- since that operation requires making a copy of the data. In this case an error
