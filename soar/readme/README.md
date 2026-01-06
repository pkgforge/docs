---
icon: rocket
description: Soar Package Manager
---

# Soar

[Soar](https://github.com/pkgforge/soar) is a fast package manager written in Rust for installing portable packages and static binaries on Linux.

## Installation

```bash
curl -fsSL "https://soar.qaidvoid.dev/install.sh" | sh
```

## Usage

```bash
soar install package_name    # Install a package
soar search query            # Search packages
soar update                  # Update packages
soar remove package_name     # Remove a package
soar log package_name        # View build log
```

## Features

- **No dependencies**: Single static binary
- **No sudo required**: Installs to user directory
- **Portable packages**: Works across Linux distributions
- **Prebuilt cache**: No compilation needed

## Documentation

- [Packages](packages.md) - Supported package types
- [Security](security.md) - Security model
