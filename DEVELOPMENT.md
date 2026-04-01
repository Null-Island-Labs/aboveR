# Development Guide

## Setup

```r
# Clone the repository
# git clone https://github.com/chrislyonsKY/aboveR.git
# cd aboveR

# Install dev dependencies
# install.packages("pak")
pak::local_install_dev_deps()

# Load the package in dev mode
devtools::load_all()
```

## Daily Workflow

```r
# Load current source (after editing R/ files)
devtools::load_all()

# Run all tests
devtools::test()

# Run a single test file
testthat::test_file("tests/testthat/test-flood.R")

# Rebuild documentation (after editing roxygen2 comments)
devtools::document()

# Full R CMD check (run before every PR)
devtools::check()
```

## Code Coverage

```r
# Local coverage report
covr::package_coverage()

# Coverage report with details
covr::report()
```

## Branch Strategy

- `main` -- stable, always passes R CMD check
- `feature/description` -- new functionality
- `fix/description` -- bug fixes
- `docs/description` -- documentation only

## Package Structure

```
R/                   # Source code (roxygen2 documented)
  security.R         # URL validation, filename sanitization, safe downloads
  terrain.R          # slope_aspect(), hillshade(), contour_lines(), zonal_stats()
  flood.R            # flood_inundation(), flood_depth(), height_above_drainage()
  change.R           # terrain_change(), change_by_zone()
  volume.R           # estimate_volume(), impoundment_curve()
  profile.R          # terrain_profile(), boundary_terrain_profile()
  highwall.R         # classify_highwall(), bench_detection()
  reclamation.R      # reclamation_progress(), surface_roughness()
  erosion.R          # detect_channels(), pond_sedimentation()
  export.R           # export_landxml(), export_stl()
  visualize.R        # change_colors(), terrain_colors(), flood_colors()
  kfa_read.R         # kfa_read_dem(), kfa_read_pointcloud(), kfa_read_ortho()
  kfa_tiles.R        # kfa_find_tiles(), kfa_tile_index()
  kfa_stac.R         # kfa_stac_search()
  kfa_counties.R     # kfa_county_bbox(), kfa_list_counties()
  kfa_constants.R    # S3 bucket paths, CRS, phase metadata
  classify.R         # Internal classification helpers
  utils.R            # Validation, CRS, bbox conversion
  aboveR-package.R   # Package-level docs and imports
tests/testthat/      # testthat edition 3
inst/extdata/        # Bundled sample data
vignettes/           # Getting started guide
```

## CI Pipeline

- **R CMD check** -- runs on push/PR to main (ubuntu, macos, windows; R release, devel, oldrel)
- **Test coverage** -- uploads to Codecov on push/PR to main
- **CodeQL** -- weekly security scan
- **Dependency review** -- checks PRs for vulnerable dependencies
- **Stale** -- auto-closes inactive issues (60d) and PRs (30d)
