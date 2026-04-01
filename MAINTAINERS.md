# Maintainers

## Current Maintainers

| Name | Role | Contact |
|------|------|---------|
| Chris Lyons | Lead maintainer | chris.lyons@ky.gov |

## Responsibilities

- Review and merge pull requests
- Manage CRAN submissions and releases
- Triage issues and security reports
- Maintain CI/CD pipelines

## Review Policy

All PRs require:
- Passing R CMD check on ubuntu, macOS, and Windows
- Passing testthat suite with no failures
- Updated roxygen2 documentation for new/changed exports
- `@returns` and `@examples` on every exported function

## Release Process

1. Update `CHANGELOG.md` with new entries
2. Bump version in `DESCRIPTION`
3. Run `devtools::document()` to regenerate man pages
4. Run `devtools::check()` to verify CRAN compliance
5. Submit to CRAN via `devtools::release()`
6. Tag the release on GitHub

## Becoming a Maintainer

Contributors who demonstrate sustained, high-quality contributions may be
invited to become maintainers. Criteria include:

- Multiple merged PRs with clean R CMD check results
- Understanding of CRAN policies and R package conventions
- Familiarity with the KyFromAbove data infrastructure
