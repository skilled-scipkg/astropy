---
name: astropy-index
description: This skill should be used when users ask how to use astropy and the correct generated documentation skill must be selected before going deeper into source code.
---

# astropy Skills Index

## Route the request
- Classify the request into one of the generated topic skills listed below.
- Prefer docs-first, workflow-level guidance before low-level symbol spelunking.
- Use `astropy-advanced-topics` for specialized one-doc themes that were intentionally consolidated.

## Generated topic skills
- `astropy-api-and-scripting`: API and Scripting (programmatic interfaces, masked/quantity behavior, SAMP, FITS APIs)
- `astropy-getting-started`: Getting Started (initial setup, quickstarts, and core concepts)
- `astropy-examples-and-tutorials`: Examples and Tutorials (worked examples, tutorials, cookbook usage)
- `astropy-inputs-and-modeling`: Inputs and Modeling (models, fitters, periodograms, input representations)
- `astropy-simulation-workflows`: Simulation Workflows (simulation setup, execution flow, and runtime controls)
- `astropy-parallel-hpc`: Parallel and HPC (MPI/OpenMP/GPU execution, scaling, and batch systems)
- `astropy-analysis-and-output`: Analysis and Output (analysis patterns, output formats, post-processing)
- `astropy-build-and-install`: Build and Install (build, installation, compilation, environment setup)
- `astropy-developer-guide`: Developer Guide (architecture, extension points, contribution workflow)
- `astropy-whatsnew`: Whatsnew (released version-change discovery and upgrade triage)
- `astropy-changes`: Changes (unreleased changelog fragment authoring and inspection)
- `astropy-io`: Io (I/O subsystems and file format workflows)
- `astropy-wcs`: Wcs (WCS usage and implementation-oriented docs)
- `astropy-table`: Table (table structures, transforms, and table-centric APIs)
- `astropy-coordinates`: Coordinates (frames, transforms, and coordinate workflows)
- `astropy-units`: Units (unit systems, quantities, conversions, equivalencies)
- `astropy-timeseries`: Timeseries (time series objects, periodograms, and analysis)
- `astropy-cosmology`: Cosmology (cosmology models, units, and I/O)
- `astropy-advanced-topics`: Advanced and Specialized Topics (project metadata/config, policy/legal docs, narrow convolution/nddata/stats/remote-method topics)

## Documentation-first inputs
- `docs`

## Tutorials and examples roots
- `docs/nddata/examples`
- `docs/wcs/examples`

## Test roots for behavior checks
- `astropy/tests`
- `docs/changes/tests`

## Escalate only when needed
- Start from topic skill primary references.
- If those references are insufficient, search that topic skill doc map in its `references` directory.
- If documentation still leaves ambiguity, open that topic skill source map in the same `references` directory and inspect the suggested source entry points.
- Use targeted symbol search while inspecting source (e.g., `rg -n "<symbol_or_keyword>" astropy cextern`).

## Source directories for deeper inspection
- `astropy`
- `cextern`
