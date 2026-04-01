# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-04-01

### Added

- **Terrain derivatives:** `slope_aspect()`, `hillshade()`, `contour_lines()`, `zonal_stats()`
- **Flood analysis:** `flood_inundation()`, `flood_depth()`, `height_above_drainage()` (HAND model)
- **Mining analysis:** `bench_detection()` for mining bench identification
- **Engineering export:** `export_landxml()` for Civil 3D TIN import, `export_stl()` for 3D printing
- **KyFromAbove counties:** `kfa_county_bbox()` and `kfa_list_counties()` for 120 KY counties
- **Color ramps:** `change_colors()`, `terrain_colors()`, `flood_colors()` now exported
- **Security module:** `sanitize_filename()`, `validate_kfa_url()`, `safe_download()` with
  timeout, retry, and size limit protection
- **CI/CD:** Codecov integration, Dependabot for GitHub Actions, CodeQL analysis,
  dependency review, stale issue bot
- **Community:** CODE_OF_CONDUCT, CONTRIBUTING, SECURITY, SUPPORT, ATTRIBUTION, DISCLAIMER,
  GOVERNANCE, MAINTAINERS, PRIVACY, RESPONSIBLE_USE, issue/PR templates, CODEOWNERS

### Changed

- KFA download functions now use `safe_download()` with 300s timeout, 3 retries,
  and 500 MB size limit (configurable)
- KFA URL handling validates against the KyFromAbove S3 bucket origin (SSRF prevention)
- Filenames from URLs are sanitized to prevent path traversal
- `kfa_stac_search()` now has CRAN-compliant `@examplesIf` documentation
- Version bumped to 1.0.0
- Author email updated to chris.lyons@ky.gov
- GitHub URLs updated to chrislyonsKY/aboveR
- Added `covr` and `withr` to Suggests

### Fixed

- Path traversal vulnerability in `kfa_read_dem()` and `kfa_read_pointcloud()` cache paths
- Missing `@examples` on `kfa_stac_search()` (CRAN compliance blocker)
- Download operations could hang indefinitely (no timeout)

## [0.1.0] - 2026-03-08

### Added

- **Core analysis:** `terrain_change()`, `change_by_zone()`, `estimate_volume()`,
  `impoundment_curve()`, `terrain_profile()`, `boundary_terrain_profile()`,
  `classify_highwall()`, `reclamation_progress()`, `surface_roughness()`,
  `detect_channels()`, `pond_sedimentation()`
- **KyFromAbove access:** `kfa_find_tiles()`, `kfa_tile_index()`, `kfa_read_dem()`,
  `kfa_read_pointcloud()`, `kfa_read_ortho()`, `kfa_stac_search()`
- Bundled sample data (50x50 grid DEMs, zones, profile line, boundary)
- Getting started vignette
- GitHub Actions R CMD check workflow
- Initial CRAN submission
