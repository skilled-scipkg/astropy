# Evidence: astropy-api-and-scripting

## Primary docs
- `docs/utils/masked/index.rst`
- `docs/samp/index.rst`
- `docs/index.rst`
- `docs/nddata/mixins/index.rst`
- `docs/io/fits/api/index.rst`
- `docs/known_issues.rst`
- `docs/coordinates/spectralcoord.rst`
- `docs/units/quantity.rst`
- `docs/nddata/subclassing.rst`
- `docs/io/unified_table_fits.rst`
- `docs/development/style-guide.rst`
- `docs/cosmology/dev.rst`

## Primary source entry points
- `skills/astropy-api-and-scripting/references/doc_map.md`
- `astropy/utils/masked/function_helpers.py`
- `astropy/units/quantity_helper/function_helpers.py`
- `astropy/units/function/logarithmic.py`
- `astropy/utils/masked/__init__.py`
- `astropy/units/quantity_helper/__init__.py`
- `astropy/units/function/__init__.py`
- `astropy/table/mixins/__init__.py`
- `astropy/nddata/mixins/__init__.py`
- `astropy/utils/masked/core.py`
- `astropy/units/function/core.py`
- `astropy/units/utils.py`
- `astropy/units/typing_utils.py`
- `astropy/units/quantity.py`
- `astropy/samp/utils.py`
- `astropy/nddata/utils.py`
- `astropy/cosmology/units.py`
- `astropy/coordinates/spectral_quantity.py`
- `astropy/units/quantity_helper/scipy_special.py`
- `astropy/units/quantity_helper/helpers.py`

## Extracted headings
- (none extracted)

## Executable command hints
- $ locale

## Warnings and pitfalls
- but it supports subclasses much better and also has some important
- .. Important:: If you use Astropy for work presented in a publication or talk
- Using ``numpy.prod`` function on a Quantity would result in error.
- result in a warning (and mmap will be disabled on the file automatically).
- On MacOS X, you may see the following error when running ``pip``::
- error::
- .. warning::
- which takes the observation time (which is important to know for any kind of
