# Contributing to aboveR

Thank you for your interest in contributing to aboveR! This guide will help you get started.

## Getting Started

1. **Fork** the repository on GitHub
2. **Clone** your fork locally:
   ```bash
   git clone https://github.com/YOUR-USERNAME/aboveR.git
   cd aboveR
   ```
3. **Install** dependencies:
   ```r
   # install.packages("pak")
   pak::local_install_dev_deps()
   ```

## Development Workflow

### Branch Naming

- `feature/description` -- new functionality
- `fix/description` -- bug fixes
- `docs/description` -- documentation changes
- `refactor/description` -- code improvements without behavior changes

### Running Tests

```r
# Unit tests
devtools::test()

# Full R CMD check (required before PR)
devtools::check()

# Test coverage report
covr::package_coverage()
```

### Code Style

- R >= 4.1.0 (native pipe `|>` is acceptable)
- roxygen2 with markdown enabled for all documentation
- Google-style function docs: Title, Description, `@param`, `@returns`, `@examples`
- testthat edition 3
- `stop()` with `call. = FALSE` for user-facing errors
- No `library()` or `require()` inside package code -- use `::` or `requireNamespace()`
- Suggested packages checked with `requireNamespace("pkg", quietly = TRUE)`

### CRAN Compliance (Non-Negotiable)

Every change must:
- Pass `R CMD check --as-cran` with 0 errors, 0 warnings
- Have `@returns` on every exported function
- Have `@examples` or `@examplesIf` on every exported function
- Never write outside `tempdir()` in examples or tests
- Guard network-dependent examples with `@examplesIf`

## Architecture

- **Core analysis functions** accept any DEM/LAS data, not just KyFromAbove
- **`kfa_*()` functions** handle KyFromAbove-specific access (EPSG:3089, S3 bucket)
- **Imports:** lidR, terra, sf (always available)
- **Suggests:** rstac, httr2, cli, rgl, mapview, ggplot2, whitebox, testthat, knitr, rmarkdown

See [ai-dev/architecture.md](ai-dev/architecture.md) for the full design.

## Submitting Changes

1. Create a feature branch from `main`
2. Make your changes with clear, focused commits
3. Ensure `devtools::check()` passes cleanly
4. Open a Pull Request with:
   - A clear title describing the change
   - A summary of what and why
   - Any relevant issue numbers

## Reporting Bugs

Open an [issue](https://github.com/chrislyonsKY/aboveR/issues) with:

- R version and OS (`sessionInfo()`)
- aboveR version (`packageVersion("aboveR")`)
- Minimal code to reproduce the problem
- Full error message

## Feature Requests

Open an [issue](https://github.com/chrislyonsKY/aboveR/issues) describing:

- The use case or problem you're trying to solve
- How you'd expect the API to work
- Any relevant KyFromAbove data products or workflows

## License

By contributing, you agree that your contributions will be licensed under the [MIT License](LICENSE).
