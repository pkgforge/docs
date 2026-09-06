---
icon: plus
description: Request a package
---

# Package Request

## Request a new package

1. Check whether it already exists: [soarpkgs.qaidvoid.dev](https://soarpkgs.qaidvoid.dev)
2. Open an [issue](https://github.com/pkgforge/soarpkgs/issues/new/choose)

Include the package name, its homepage, a link to its releases, and what you want it for.

## Add it yourself

See the [contribution guide](contribution.md) and the [recipe reference](../../packaging/recipe.md). Most packages are a short `pkg.toml` and nothing else.

## What gets accepted

Packages should have an active upstream, clear licensing, and no existing equivalent already in the repository. Open source is strongly preferred.

The format also asks something of the package: it has to be pinnable. A project that publishes a release artifact per architecture is a few lines. One that publishes nothing, or ships glibc-linked binaries only, has to be built in [pkgforge/builds](../../packaging/builds.md) first, which is a larger ask and is why that repository stays small.
