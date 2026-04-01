# Security Policy

## Supported Versions

| Version | Supported |
|---------|-----------|
| 1.0.x   | Yes       |
| < 1.0   | No        |

## Reporting a Vulnerability

If you discover a security vulnerability in aboveR, please report it responsibly:

1. **Do not** open a public GitHub issue
2. Email **chris.lyons@ky.gov** with details
3. Include steps to reproduce, if possible
4. You will receive acknowledgment within 48 hours

## Scope

aboveR accesses publicly available geospatial data from the KyFromAbove S3 bucket. It does not handle authentication, store credentials, or process sensitive user data.

Potential security concerns include:
- Path traversal in download file naming
- URL injection via tile index data
- Dependency vulnerabilities

## Dependencies

aboveR pins minimum versions for its dependencies. We recommend keeping dependencies updated:

```r
pak::pak("chrislyonsKY/aboveR")
```
