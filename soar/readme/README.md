---
icon: rocket
description: Soar Package Manager
---

# Soar

[Soar](https://github.com/pkgforge/soar) is a fast, distro-independent package manager written in Rust. It installs static binaries, AppImages and other portable formats under your home directory, with no superuser and no runtime dependencies.

Soar installs packages. It does not build or host them. Repositories publish metadata in a standard format, and Soar reads that metadata to search, install and update. [soarpkgs](../../repositories/soarpkgs/) is the default repository, but Soar is not tied to it: you can add a third party one or [run your own](../../repositories/external/).

## Installation

```bash
curl -fsSL "https://soar.qaidvoid.dev/install.sh" | sh
```

It is a single statically linked binary, so [downloading a release](https://github.com/pkgforge/soar/releases/latest) and putting it on your `PATH` works just as well.

## Usage

```bash
soar sync                  # fetch repository metadata
soar search ripgrep        # find a package
soar install ripgrep       # install it
soar run ripgrep           # run it once, without installing
soar list                  # everything available
soar info                  # what you have installed
soar update                # update everything
soar remove ripgrep        # remove it
```

A package can also come straight from a URL or a local file, and one installed from a GitHub or GitLab release keeps tracking that release:

```bash
soar install https://github.com/owner/repo/releases/download/v1/tool
```

`soar --help` lists the rest.

## Features

* **Universal**: one statically linked binary, no dependencies, no superuser, any Linux distribution
* **Portable formats**: static binaries, AppImages and other self-contained formats, installed the same way
* **Install from anywhere**: a repository, a direct URL, or a local file
* **Delta updates**: AppImages advertising a zsync feed update by fetching only what changed
* **System integration**: desktop entries, icons, manual pages and shell completions land where your system already looks
* **Verified by default**: checksums and signatures are checked before anything is installed

## Documentation

* [Packages](packages.md), what Soar can install
* [Security](security.md), how installs are verified
* [Full documentation](https://soar.qaidvoid.dev/), configuration, profiles and every command
