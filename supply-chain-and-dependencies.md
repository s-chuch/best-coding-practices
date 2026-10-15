# Dependency Management and Software Supply Chain

## Core Practices

- Minimize the dependency footprint. Prefer well-maintained libraries with active security response.
- Pin and lock dependencies (lockfiles) for reproducible builds.
- Review dependency changes before merging.
- Automate vulnerability scanning (SCA) in CI.
- Prefer signed packages and verify checksums when available.

## Software Bill of Materials (SBOM)

- Generate SBOMs (e.g., CycloneDX) automatically for each release.
- Include direct and transitive dependencies, versions, and identifiers.
- Store and query SBOMs so you can quickly answer "which of our products contain this vulnerable component?"
- Treat SBOMs as living artifacts, not one-time checkboxes.
- Consider VEX documents to state whether a vulnerability actually affects your product.

## Provenance and Policy

- Record how artifacts are built (SLSA-style provenance when practical).
- Enforce policy: e.g., no unsigned code merges, no unattested artifacts deploy.
- Scan for malicious packages and risky install scripts before they enter the build.

## Continuous Monitoring

- Do not rely only on point-in-time audits.
- Monitor deployed components against newly disclosed vulnerabilities.
- Tools such as Dependency-Track or similar platforms help inventory and analyze risk across projects.

## Procurement

- Prefer vendors that can supply SBOMs.
- Evaluate third-party software with the same inventory and vulnerability visibility you apply to your own code.

Supply-chain risk is real. Visibility (SBOM + dependency graph) plus continuous monitoring is the practical foundation for response.
