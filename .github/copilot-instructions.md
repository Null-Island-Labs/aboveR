# GitHub Copilot Instructions — aboveR

> LiDAR Terrain Analysis and Change Detection from Above
> R geospatial toolkit by [chrislyonsKY](https://github.com/chrislyonsKY)

## Package Context

Terrain analysis functions that lidR (forestry) and terra (general raster) don't provide: change detection between DEM epochs, cut/fill volume estimation, terrain profiling, flood inundation analysis, slope/aspect/hillshade, contour extraction, erosion channel detection, reclamation monitoring, impoundment capacity curves, HAND flood risk, and engineering export (LandXML, STL). Built ON TOP of lidR (for LAS I/O) and terra (for raster operations).

Includes KyFromAbove access module for Kentucky's cloud-native elevation data on AWS S3. Dual access path: STAC catalog (github.com/ianhorn/kyfromabove-stac, under development) with fallback to S3 tile index GeoPackages. KyFromAbove data is in EPSG:3089 (Kentucky Single Zone), 5000x5000ft tile grid, unsigned S3 access at s3://kyfromabove/ (us-west-2).

## Exported API

Core analysis: terrain_change(), change_by_zone(), estimate_volume(), impoundment_curve(), terrain_profile(), boundary_terrain_profile(), classify_highwall(), bench_detection(), reclamation_progress(), surface_roughness(), detect_channels(), pond_sedimentation()

Terrain derivatives: slope_aspect(), hillshade(), contour_lines(), zonal_stats()

Flood analysis: flood_inundation(), flood_depth(), height_above_drainage()

Export: export_landxml(), export_stl()

Visualization: change_colors(), terrain_colors(), flood_colors()

KyFromAbove access: kfa_find_tiles(), kfa_tile_index(), kfa_read_dem(), kfa_read_pointcloud(), kfa_read_ortho(), kfa_stac_search(), kfa_county_bbox(), kfa_list_counties()

## Dependencies

- **Imports (always available):** lidR, terra, sf
- **Suggests (check at runtime):** rstac, httr2, rgl, mapview, ggplot2, whitebox, cli, covr, withr, testthat

When using rstac or other Suggested packages:
```r
if (!requireNamespace("rstac", quietly = TRUE)) {
  stop("Package 'rstac' is required for STAC access.\n",
       "Install it with: install.packages('rstac')", call. = FALSE)
}
```

## Security

- All KFA URLs are validated against the KyFromAbove S3 bucket origin
- Filenames from URLs are sanitized to prevent path traversal
- Downloads use timeouts, size limits, and retry logic (see R/security.R)

## CRAN Compliance (Non-Negotiable)

- All exported functions need `@returns` and `@examples` or `@examplesIf`
- KyFromAbove examples use `@examplesIf aboveR::has_s3_access()`
- Core analysis examples use bundled sample rasters in `inst/extdata/`
- Never write outside `tempdir()` in examples or tests
- Cache files go to `tools::R_user_dir("aboveR", "cache")`
- Network tests use `skip_on_cran()`
- `\donttest{}` for slow computations, never `\dontrun{}`

## R Coding Conventions

- R >= 4.1.0 (native pipe `|>` is acceptable)
- roxygen2 with markdown enabled
- testthat edition 3
- terra SpatRaster for all raster returns
- sf tibble for all vector returns
- lidR LAS for point cloud returns
- Error handling: `stop()` with informative messages and `call. = FALSE`
- Progress bars via cli (Suggests) for long operations
