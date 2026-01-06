---
icon: message-question
description: Frequently Asked Questions
---

# FAQ

### Is this an AUR?

Soarpkgs is inspired by the AUR concept but with a curated approach. Packages are reviewed by maintainers before inclusion, unlike AUR's open submission model.

---

### Cache

Cache refers to prebuilts from pkgforge's CI that Soar uses by default.

* [Bincache](../bincache/): Prebuilt static binaries
* [Pkgcache](../pkgcache/): Prebuilt GUI apps

---

### GLIBC vs MUSL

MUSL binaries use [mimalloc](https://github.com/microsoft/mimalloc) for performance parity with GLIBC. We also apply LTO and PIE optimizations.

---

### Portability

* Prebuilt packages are provided via cache to avoid build dependencies
* Heavy builds requiring containers are marked with a note
* Portable packages are tagged with `[PORTABLE]` in notes

---

### External Sources

Soar integrates with external sources:
* [appimage.github.io](https://docs.pkgforge.dev/repositories/external/appimage.github.io)
* [AM](https://docs.pkgforge.dev/repositories/external/am)

---

### History

* **July 2023**: Toolpacks created
* **Sep 2024**: PkgCache created
* **Nov 2024**: Soarpkgs created
