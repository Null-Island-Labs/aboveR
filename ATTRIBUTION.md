# Attribution

## Data Sources

aboveR is designed to work with LiDAR-derived elevation data from any source.
The KyFromAbove access module (`kfa_*` functions) provides direct integration
with the following program:

### KyFromAbove

- **Program:** [KyFromAbove](https://kyfromabove.ky.gov) -- Kentucky's statewide
  aerial LiDAR and imagery acquisition program
- **Producer:** Kentucky Division of Geographic Information (DGI),
  Commonwealth Office of Technology
- **Hosting:** [AWS Open Data Registry](https://registry.opendata.aws/kyfromabove/)
  -- public S3 bucket (us-west-2, unsigned access)
- **STAC Catalog:** Ian Horn ([github.com/ianhorn](https://github.com/ianhorn))
- **License:** Public domain (government data)

### Other Data Programs

aboveR's core analysis functions work with any DEM or LAS data, including:

- **USGS 3DEP** -- National 3D Elevation Program
- **FEMA** -- Flood risk mapping and levee analysis
- **State LiDAR programs** -- Various state acquisition programs
- **Commercial acquisitions** -- Site-specific survey data

## Software Dependencies

aboveR is built on the R geospatial ecosystem:

- [lidR](https://github.com/r-lidar/lidR) -- LAS/LAZ/COPC I/O and point cloud processing
- [terra](https://github.com/rspatial/terra) -- Raster operations and COG access
- [sf](https://github.com/r-spatial/sf) -- Vector operations and spatial queries

## Citation

If you use aboveR in published work, please cite:

```
Lyons, C. (2026). aboveR: LiDAR Terrain Analysis and Change Detection from Above.
R package version 1.0.0. https://github.com/chrislyonsKY/aboveR
```
