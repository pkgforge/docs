---
icon: boxes-packing
description: What Soar can install
---

# Packages

## Hosts

[soarpkgs](../../repositories/soarpkgs/) publishes for `x86_64-linux`, `aarch64-linux` and `riscv64-linux`. Whether a given package serves all three depends on what upstream ships.

Soar itself runs anywhere Linux does. What you can install through it is a question about the repository, not about Soar.

## Formats

| Format | Notes |
|---|---|
| [Static binaries](../../formats/binaries/static/) | Statically linked, needing no libc on the host. |
| [AppImages](../../formats/packages/appimage/) | Self-contained applications, mounted or extracted at run time. |
| [onelf](../../formats/packages/onelf/) | A self-extracting ELF carrying a binary and its libraries. |
| [Other portable formats](../../formats/packages/) | AppBundle, FlatImage, RunImage, NixAppImage and archives. |

Soar handles all of them the same way, whether they arrive from a repository, a URL, or a local file. Which ones you find in a given repository depends on what its upstreams publish.

## Sources

Besides a repository, Soar installs from:

* a direct URL, including a GitHub or GitLab release, which it then keeps tracking
* a `ghcr.io/...` reference
* a local file

```bash
soar install ./tool.appimage
soar install https://github.com/owner/repo/releases/download/v1/tool
soar install ghcr.io/owner/repo:tag
```

## Standalone

Packages are ordinary portable artifacts. Nothing about them requires Soar, so anything installed through it can be copied elsewhere and run on its own.
