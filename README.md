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

[PkgForge](https://github.com/pkgforge) provides portable packages and static binaries for Linux, along with [Soar](https://github.com/pkgforge/soar) - a fast package manager written in Rust.

## Quick Start

```bash
# Install Soar
curl -fsSL "https://soar.qaidvoid.dev/install.sh" | sh

# Install a package
soar install pkg_name
```

## Resources

- [Soar Documentation](soar/readme/)
- [Package Formats](formats/packages/)
- [SBUILD Specification](sbuild/introduction.md)
- [Package Search](https://pkgs.pkgforge.dev/)
