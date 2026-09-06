---
icon: box-open-full
description: The official Soar repository
---

# soarpkgs

[soarpkgs](https://github.com/pkgforge/soarpkgs) is the official package repository for [Soar](../../soar/readme/), and the only one PkgForge publishes. It is enabled by default, so a fresh Soar installation needs nothing added to it.

Packages are [declared in TOML](../../packaging/) and pinned by hash. Nothing in the tree executes: a package is resolved by parsing it, and every download is verified against a hash that was reviewed in a commit rather than measured after the fact.

## Structure

```
packages/<name>/
  pkg.toml                 identity, metadata, update policy, how to find the artifact
  <name>-<version>.toml    the resolved URL, its hashes, and any side files
```

## Hosts

soarpkgs publishes for `x86_64-linux`, `aarch64-linux` and `riscv64-linux`. Not every package serves all three, since that depends on what upstream ships.

## Package types

A package's `type` names the [format](../../formats/packages/) its artifact is in, and any format Soar handles can be named there. What you find in the tree today is mostly `static`, statically linked binaries needing no libc on the host, and `appimage`, plus a couple of [`onelf`](../../formats/packages/onelf/) packages. That reflects what upstreams publish, not a restriction.

## Links

* [Repository](https://github.com/pkgforge/soarpkgs)
* [Package search](https://soarpkgs.qaidvoid.dev)
* [Packaging](../../packaging/)
* [Contribution guide](contribution.md)
* [Metadata](metadata.md)
