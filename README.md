---
icon: box-archive
description: Package Forge
cover: .gitbook/assets/pkgforge (1).png
coverY: 0
layout:
  cover:
    visible: false
    size: full
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# PkgForge

## About

[PkgForge](https://github.com/pkgforge) provides portable packages and static binaries for Linux, along with [Soar](https://github.com/pkgforge/soar), a fast package manager written in Rust.

Packages live in [soarpkgs](repositories/soarpkgs/), where each one is a declarative TOML file pinning an upstream release by URL and hash. Nothing in that tree executes, so a package is verified against something a reviewer approved rather than something a build produced.

## Quick start

```bash
# Install Soar
curl -fsSL "https://soar.qaidvoid.dev/install.sh" | sh

# Install a package
soar install ripgrep
```

## Resources

* [Soar](soar/readme/), what it is and how to use it
* [Packaging](packaging/), how a package is declared
* [soarpkgs](repositories/soarpkgs/), the official repository
* [Package formats](formats/packages/), AppImage, onelf and the rest
* [Package search](https://soarpkgs.qaidvoid.dev)
