# Privacy

## No Telemetry

aboveR does **not** collect, transmit, or store any personal data, usage
statistics, or telemetry. There are no analytics, tracking, or phone-home
mechanisms of any kind.

## Network Requests

aboveR makes network requests only when explicitly requested by the user
through `kfa_*()` functions. These requests go to:

- **KyFromAbove S3 bucket** (`kyfromabove.s3.us-west-2.amazonaws.com`) --
  public, unsigned access to elevation data, point clouds, and imagery
- **STAC catalog** (when available) -- public metadata queries via `rstac`

No credentials, API keys, or authentication tokens are required or transmitted.

## Local Caching

When `kfa_tile_index()` or `kfa_read_dem(..., cache = TRUE)` is used, files
are cached in the CRAN-approved user cache directory:

```r
tools::R_user_dir("aboveR", "cache")
```

Cached files contain only publicly available geospatial data (tile index
GeoPackages and DEM rasters). No personal information is stored.

## Data Processed

All data processed by aboveR (DEMs, point clouds, polygons) stays local
to the user's machine. Results are never uploaded or shared externally.
