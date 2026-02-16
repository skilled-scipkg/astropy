# Evidence: astropy-examples-and-tutorials

## Primary docs
- `docs/units/format.rst`
- `docs/timeseries/bls.rst`
- `docs/timeseries/analysis.rst`
- `docs/units/equivalencies.rst`
- `docs/table/operations.rst`
- `docs/table/mixin_columns.rst`
- `docs/table/dataframes.rst`
- `docs/io/unified_table.rst`
- `docs/coordinates/velocities.rst`
- `docs/coordinates/representations.rst`
- `docs/coordinates/frames.rst`
- `docs/coordinates/angles.rst`

## Primary source entry points
- `skills/astropy-examples-and-tutorials/references/doc_map.md`
- `astropy/units/format/fits.py`
- `astropy/timeseries/periodograms/bls/__init__.py`
- `astropy/timeseries/periodograms/bls/core.py`
- `astropy/table/_dataframes.py`
- `astropy/coordinates/angles/formats.py`
- `astropy/timeseries/periodograms/bls/setup_package.py`
- `astropy/timeseries/periodograms/bls/methods.py`
- `astropy/timeseries/periodograms/bls/bls.c`
- `astropy/timeseries/periodograms/bls/_impl.pyx`
- `astropy/timeseries/periodograms/lombscargle/implementations/fast_impl.py`
- `astropy/units/format/__init__.py`
- `astropy/coordinates/builtin_frames/__init__.py`
- `astropy/coordinates/angles/__init__.py`
- `astropy/coordinates/angles/core.py`
- `astropy/units/equivalencies.py`
- `astropy/table/operations.py`
- `astropy/table/ndarray_mixin.py`
- `astropy/units/function/mixin.py`
- `astropy/units/format/vounit.py`

## Extracted headings
- ****
- Convert to pandas DataFrame
- Convert to polars DataFrame
- Use a column as the DataFrame index
- Convert back including the index as a column
- %ECSV 1.0
- schema: astropy-2.0

## Executable command hints
- $ showtable-astropy astropy/io/fits/tests/data/table.fits

## Warnings and pitfalls
- By default converting such units to strings emits a warning::
- constructing the string and a warning is emitted.
- The warning message (if ``parse_strict='warn'``) will then contain information
- ``numpy`` arrays or :class:`~astropy.units.Quantity` objects. If known, error
- The output grouped table has two important properties:
- :meth:`~astropy.table.groups.TableGroups.aggregate` will issue a warning and
- ``keys`` argument is an error)::
- By default, a warning is emitted in the last case (both metadata values are not
- `None`). The warning can be silenced or made into an exception using the
- - ``'silent'`` – no warning is emitted, the value for the last table is silently
- - ``'warn'`` – a warning is emitted, the value for the last table is picked.
- - ``'error'`` – an exception is raised.
