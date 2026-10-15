# Reproducible Builds

A build is reproducible when the same source, environment, and instructions produce bit-for-bit identical artifacts. This lets anyone verify that the published binary matches the source and that nothing was injected in the supply chain.

## Practices

- **Lockfiles**: Pin direct and transitive dependencies to exact versions. Commit the lockfile. Prefer `npm ci`, `pip install -r` with hashes, or equivalent over floating installs.
- **Immutable references**: Pin container base images by digest, CI actions by commit SHA, and toolchains by exact version. Tags can move; digests and SHAs do not.
- **Hermetic builds**: Declare all inputs. Avoid network access during the build when possible. Use sandboxed or containerized environments.
- **Determinism**: Eliminate sources of non-determinism (timestamps in artifacts, unstable file order, absolute paths). Many languages have flags (`-trimpath`, reproducible plugins) for this.
- **Provenance**: Record how the artifact was built (SLSA-style provenance). Sign releases.
- **SBOM**: Generate a Software Bill of Materials for each release so vulnerabilities can be traced later.

## Incremental Path

1. Commit lockfiles and use the deterministic install command in CI.
2. Pin base images and CI actions.
3. Add SBOM generation on release.
4. Work toward hermetic or fully reproducible builds for critical artifacts.

## Why It Matters

Reproducible builds close a common supply-chain gap: even if source is reviewed, a compromised or non-deterministic build environment can produce different binaries. Verification becomes possible only when the build is deterministic.

Start with lockfiles and pinning; full bit-for-bit reproducibility is a longer journey but the early steps already reduce risk.
