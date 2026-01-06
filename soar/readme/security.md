---
icon: lock
description: Security Model
---

# Security

## Build Security

- **Unprivileged**: No sudo/doas required
- **Isolated builds**: CI runs in rootless containers
- **Transparent logs**: View build logs with `soar log $pkg`

## Verification

- **Checksums**: b3sum + sha256sum
- **Attestations**: [GitHub Artifact Attestations](https://docs.github.com/en/actions/security-for-github-actions/using-artifact-attestations)
- **Signing**: minisign signatures

Soar's build process meets [SLSA Build L2](https://slsa.dev/spec/v1.0/levels#build-l2).
