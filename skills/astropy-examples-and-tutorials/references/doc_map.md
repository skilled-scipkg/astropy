# astropy documentation map: Examples and Tutorials

Generated from documentation roots:
- `docs`
- `docs/nddata/examples`
- `docs/wcs/examples`
- `astropy/tests`
- `docs/changes/tests`

Total docs grouped in this topic: 47

## File inventory
- `docs/units/format.rst` | title: String Representations of Units and Quantities | headings: String Representations of Units and Quantities; Converting to Strings; Examples
- `docs/timeseries/bls.rst` | title: Box Least Squares (BLS) Periodogram | headings: Box Least Squares (BLS) Periodogram; Mathematical Background; Basic Usage
- `docs/timeseries/analysis.rst` | title: Manipulation and Analysis of Time Series | headings: Manipulation and Analysis of Time Series; Combining Time Series; Examples
- `docs/units/equivalencies.rst` | title: Equivalencies | headings: Equivalencies; Built-In Equivalencies; How to Convert Parallax to Distance
- `docs/table/operations.rst` | title: Table Operations | headings: Table Operations; Grouped Operations; Table Groups
- `docs/table/mixin_columns.rst` | title: Mixin Columns | headings: Mixin Columns; Basic Example; Quantity and QTable
- `docs/table/dataframes.rst` | title: Interfacing with DataFrames | headings: Interfacing with DataFrames; Generic Multi-Backend Methods; Supported Backends
- `docs/io/unified_table.rst` | title: %ECSV 1.0 | headings: %ECSV 1.0; schema: astropy-2.0; Table Data
- `docs/coordinates/velocities.rst` | title: Working with Velocities in Astropy Coordinates | headings: Working with Velocities in Astropy Coordinates; Using Velocities with ``SkyCoord``; Examples
- `docs/coordinates/representations.rst` | title: Using and Designing Coordinate Representations | headings: Using and Designing Coordinate Representations; Instantiating and Converting; Array Values and NumPy Array Method Analogs
- `docs/coordinates/frames.rst` | title: Using and Designing Coordinate Frames | headings: Using and Designing Coordinate Frames; Using Frame Objects; Frames without Data
- `docs/coordinates/angles.rst` | title: Working with Angles | headings: Working with Angles; Creation; Examples
- `docs/io/ascii/fast_ascii_io.rst` | title: Fast ASCII I/O | headings: Fast ASCII I/O; Examples; Reading
- `docs/io/ascii/write.rst` | title: %ECSV 1.0 | headings: %ECSV 1.0; ---; datatype:
- `docs/io/ascii/read.rst` | title: Read a large CSV table in 100 Mb chunks. | headings: Read a large CSV table in 100 Mb chunks.; tbls is an iterator over the chunks (no actual reading done yet); At this point the file is actually read in chunks.
- `docs/timeseries/times.rst` | title: Converting between Different Time Representations | headings: Converting between Different Time Representations; Converting Times; Example
- `docs/stats/robust.rst` | title: Robust Statistical Estimators | headings: Robust Statistical Estimators; Sigma Clipping; Examples
- `docs/samp/example_table_image.rst` | title: Sending and Receiving Tables and Images over SAMP | headings: Sending and Receiving Tables and Images over SAMP; Sending a Table to TOPCAT and DS9; Receiving a Table from TOPCAT
- `docs/io/fits/usage/image.rst` | title: Image Data | headings: Image Data; Image Data as an Array; Examples
- `docs/io/fits/usage/verification.rst` | title: Verification | headings: Verification; FITS Standard; Verification Options
- `docs/io/fits/usage/unfamiliar.rst` | title: Less Familiar Objects | headings: Less Familiar Objects; ASCII Tables; Creating an ASCII Table
- `docs/io/fits/usage/table.rst` | title: Table Data | headings: Table Data; Table Data as a Record Array; What is a Record Array?
- `docs/io/fits/usage/headers.rst` | title: FITS Headers | headings: FITS Headers; Header of an HDU; The Header Attribute
- `docs/units/decomposing_and_composing.rst` | title: Decomposing and Composing Units | headings: Decomposing and Composing Units; Reducing a Unit to Its Irreducible Parts; Examples
- `docs/timeseries/io.rst` | title: Reading and Writing Time Series | headings: Reading and Writing Time Series; Built-in Readers; Example
- `docs/units/combining_and_defining.rst` | title: Combining and Defining Units | headings: Combining and Defining Units; Basic example; Fractional powers
- `docs/samp/example_hub.rst` | title: Starting and Stopping a SAMP Hub Server | headings: Starting and Stopping a SAMP Hub Server; Using an Existing Hub; Using the Command-Line Hub Utility
- `docs/io/unified_table_hdf5.rst` | title: HDF5 | headings: HDF5; Examples; Metadata and Mixin Columns
- `docs/coordinates/transforming.rst` | title: Transforming between Systems | headings: Transforming between Systems; Examples; Transformations and Solar System Ephemerides
- `docs/coordinates/galactocentric.rst` | title: Description of the Galactocentric Coordinate Frame | headings: Description of the Galactocentric Coordinate Frame; Definition of the Transformation; Controlling the Default Frame Parameters
- `docs/coordinates/solarsystem.rst` | title: Solar System Ephemerides | headings: Solar System Ephemerides; Examples; Precision of the Built-In Ephemeris
- `docs/coordinates/apply_space_motion.rst` | title: Accounting for Space Motion | headings: Accounting for Space Motion; Example; Example: Use velocity to compute sky position at different epochs
- `docs/units/constants_versions.rst` | title: Using Prior Versions of Constants | headings: Using Prior Versions of Constants; Example
- `docs/timeseries/pandas.rst` | title: Interfacing with the Pandas Package | headings: Interfacing with the Pandas Package; Example
- `docs/timeseries/masking.rst` | title: Masking Values in Time Series | headings: Masking Values in Time Series; Example
- `docs/io/unified_table_votable.rst` | title: VO Tables | headings: VO Tables; Examples
- `docs/io/unified_table_parquet.rst` | title: Parquet | headings: Parquet; Examples
- `docs/development/scripts.rst` | title: Command-Line Scripts | headings: Command-Line Scripts; Example
- `docs/coordinates/formatting.rst` | title: Formatting Coordinate Strings | headings: Formatting Coordinate Strings; Examples
- `docs/wcs/example_cube_wcs.rst` | title: Second Example | headings: Second Example
- `docs/wcs/example_create_imaging.rst` | title: First Example | headings: First Example
- `docs/samp/example_clients.rst` | title: Communication between Integrated Clients Objects | headings: Communication between Integrated Clients Objects
- `docs/coordinates/example_gallery_rv_to_gsr.rst` | title: Convert a radial velocity to the Galactic Standard of Rest (GSR) | headings: Convert a radial velocity to the Galactic Standard of Rest (GSR)
- `docs/coordinates/example_gallery_plot_obs_planning.rst` | title: Determining and plotting the altitude/azimuth of a celestial object | headings: Determining and plotting the altitude/azimuth of a celestial object
- `docs/coordinates/example_gallery_plot_galactocentric_frame.rst` | title: Transforming positions and velocities to and from a Galactocentric frame | headings: Transforming positions and velocities to and from a Galactocentric frame
- `docs/coordinates/example_gallery_index.rst` | title: Example Gallery | headings: Example Gallery
- `docs/io/fits/usage/misc.rst` | title: Miscellaneous Features | headings: Miscellaneous Features; Differs; Example
