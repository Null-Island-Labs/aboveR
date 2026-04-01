# Disclaimer

## Data Accuracy

- DEM elevation values are approximate and derived from airborne LiDAR
  acquisition. They are **not a substitute for professional land surveys**.
- Temporal accuracy depends on the acquisition date of the source data.
  KyFromAbove phases were flown over multiple years.
- Spatial accuracy varies by phase, product, and terrain conditions.
  Consult the KyFromAbove program documentation for accuracy specifications.
- Volume calculations (`estimate_volume()`, `pond_sedimentation()`, etc.)
  are estimates based on grid integration methods. Results depend on DEM
  resolution, interpolation method, and boundary precision.

## Software

aboveR is provided under the MIT License. There is **no warranty** of any kind,
express or implied, including but not limited to fitness for a particular purpose.
See [LICENSE](LICENSE) for the full text.

## Third-Party Services

- **KyFromAbove S3 bucket** -- public data hosted by the Commonwealth of
  Kentucky. Availability is not guaranteed by this package.
- **STAC catalog** -- under development. May not be available at all times.
- Tile index GeoPackages are cached locally and may become stale.
  Use `max_age_days` parameter to control cache freshness.

## Appropriate Use

Do not rely solely on aboveR outputs for:
- Legal boundary determinations
- Life-safety engineering decisions
- Regulatory compliance submissions

Always verify results with authoritative survey data for critical applications.
