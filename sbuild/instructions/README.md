---
icon: wrench
description: How to write an SBUILD
---

# Instructions

## Prerequisites

* [x] [Install Soar](https://soar.qaidvoid.dev/installation)
* [x] Read the [Spec](https://docs.pkgforge.dev/sbuild/specification)
* [x] View [examples](https://github.com/pkgforge/soarpkgs/tree/main/packages)

---

## Write

1. Copy the [template](https://github.com/pkgforge/soarpkgs/blob/main/templates/generic.SBUILD.yaml)
2. Fill in the fields following the [spec](../specification/) and [examples](examples.md)
3. Validate with [sbuild-linter](https://github.com/pkgforge/sbuilder):

```bash
soar add "sbuild-linter"
sbuild-linter "./example.SBUILD"

# To test pkgver fetching
sbuild-linter "./example.SBUILD" --pkgver
```

4. Submit a [Pull Request](https://github.com/pkgforge/soarpkgs/compare) or [Issue](https://github.com/pkgforge/soarpkgs/issues/new/choose) with the `.validated` version

---

## Build

{% hint style="warning" %}
Use a sandbox or container when running untested SBUILDs.
{% endhint %}

```bash
soar add "sbuild"
sbuild "./example.SBUILD" --log-level "verbose" --keep --outdir "./SBUILD-TEST"
```
