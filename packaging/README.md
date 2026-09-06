---
icon: circle-info
description: How packages are declared
---

# Packaging

Packages in [soarpkgs](../repositories/soarpkgs/) are declared in TOML. Nothing in the tree executes. A client resolves a package by parsing it, and verifies the download against a hash that was reviewed in a commit rather than measured after the fact.

Every package is a directory holding two kinds of file:

```
packages/<name>/
  pkg.toml                 identity, metadata, update policy, how to find the artifact
  <name>-<version>.toml    the resolved URL, its hashes, and any side files
```

The [recipe](recipe.md) says where upstream publishes its artifact. The [version file](version-file.md) pins one release of it. [`sbuild`](tooling.md) turns the first into the second, and turns the whole tree into the index Soar reads.

```
recipe        pkg.toml                    what upstream publishes, as a template
   |  resolve
version file  <name>-<version>.toml       one release, pinned by URL and hash
   |  meta
index         metadata-<host>.json        what Soar reads
```

A package may hold several version files. Each becomes its own entry in the generated index, so an older version stays installable after a newer one is pinned.

## What happened to SBUILD

SBUILD was a YAML build script. It ran shell to produce a package, and the resulting hash was whatever that build happened to emit, recorded afterwards. It has been retired.

The declarative format drops the build step for everything upstream already publishes. The recipe names the release asset, and the hash of that asset is committed and reviewed like any other line in the repository. Anyone can check a package without trusting us: download the pinned URL, hash it, compare.

The handful of packages that genuinely need building are built in [pkgforge/builds](builds.md), which publishes ordinary GitHub releases that soarpkgs pins like any other upstream.

## Getting started

1. Read the [recipe reference](recipe.md) and the [version file reference](version-file.md)
2. Look at the [examples](examples.md), and at [existing packages](https://github.com/pkgforge/soarpkgs/tree/main/packages)
3. Scaffold a recipe with `sbuild new`, fill it in, and open a [pull request](https://github.com/pkgforge/soarpkgs/compare)

The canonical spec lives with the tree it describes, in [soarpkgs/docs/FORMAT.md](https://github.com/pkgforge/soarpkgs/blob/main/docs/FORMAT.md). This section is the longer version of it.
