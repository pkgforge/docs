---
icon: lock
description: How installs are verified
---

# Security

## What Soar checks

Every artifact in a repository index carries a blake3 hash. Soar verifies the download against it before anything is unpacked, and refuses the package if it does not match.

The index itself is signed with [minisign](https://jedisct1.github.io/minisign/). Soar checks the signature before reading the index, using a public key it ships for [soarpkgs](../../repositories/soarpkgs/) and whichever key you configured for any [other repository](../../repositories/external/).

The two checks are independent, so a validly signed index carrying a wrong hash still fails at install. That matters, because it means a repository cannot sign its way past a hash somebody reviewed.

## What the repository guarantees

soarpkgs is [declarative](../../packaging/). Nothing in it executes, so there is no build script whose behaviour has to be taken on trust. A package is a URL, a hash, and a list of paths, all visible in the diff of the commit that added it.

Anyone can verify a package without trusting us: download the pinned URL, hash it, and compare against the [version file](../../packaging/version-file.md) in the tree.

Packages that cannot be pinned from an upstream release are built in [pkgforge/builds](../../packaging/builds.md), which pins its sources by commit and its toolchains by image digest, attests build provenance through [GitHub artifact attestations](https://docs.github.com/en/actions/security-for-github-actions/using-artifact-attestations), and rebuilds published packages on a schedule to check they still reproduce.

## What Soar does on your system

* **No superuser.** Packages install under your home directory. A system-wide mode exists behind `soar --system`, and needs root only because that is what writing outside your home requires.
* **No distribution packages touched.** Soar never writes outside its own directories.
* **https only.** A repository URL over plain http is refused.

## Reporting

For Soar itself, open a [security advisory](https://github.com/pkgforge/soar/security/advisories/new) or reach us through [chat](../../contact/chat.md). For a package, see [soarpkgs security](../../repositories/soarpkgs/security.md).
