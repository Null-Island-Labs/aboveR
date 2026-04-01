# Governance

## Project Scope

aboveR is an R package for LiDAR terrain analysis and change detection, with
integration to the KyFromAbove program for Kentucky-specific data access.

### What Gets Accepted

- Terrain analysis functions applicable to DEM/LAS data from any source
- KyFromAbove data access improvements and bug fixes
- Performance optimizations for large raster operations
- Documentation improvements and vignettes
- CRAN compliance fixes
- Security patches

### What Gets Rejected

- Features unrelated to terrain analysis or LiDAR processing
- Generic STAC client features (use `rstac` directly)
- Non-geospatial functionality
- Dependencies that would make the package difficult to install

## Decision Making

- **Routine changes** (bug fixes, docs, minor features): accepted via PR review
  by a maintainer
- **Significant changes** (new modules, API changes, new Imports): require a
  GitHub issue discussion before implementation
- **Breaking changes**: require major version bump and deprecation period

## CRAN Compliance

All changes must pass `R CMD check --as-cran` with 0 errors, 0 warnings.
This is non-negotiable and takes priority over feature requests.
