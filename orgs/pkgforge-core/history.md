---
icon: clock-rotate-left
description: How PkgForge got here
---

# History

## Toolpacks

[**@Azathothas**](https://github.com/Azathothas) used to be a bug bounty hunter. Setting up pentesting environments on remote servers was frustratingly slow, since tools like [reconftw](https://github.com/six2dez/reconftw) would install entire toolchains just to get a few binaries out of them.

Around **July 2023** he started maintaining scripts to fetch precompiled binaries instead. What began as wrappers around [eget](https://github.com/zyedidia/eget) grew into several repositories, and eventually consolidated into [Toolpacks](https://github.com/Azathothas/Toolpacks). Toolpacks was archived on **2025-01-01** as part of a rewrite.

Two package managers came out of that period before Soar did. [**@pwnwriter**](https://github.com/pwnwriter) created [Hysp](https://github.com/pwnwriter/hysp) in **November 2023**, the first one to read Toolpacks. [**@Xplshn**](https://github.com/xplshn) went from [bdl](https://github.com/xplshn/Handyscripts/blob/master/bdl) to BigDL to [Dbin](https://github.com/xplshn/dbin).

## Soar

After [Toolpacks#28](https://github.com/Azathothas/Toolpacks/issues/28), portable package formats came into scope: [AppImages](https://appimage.org/), [AppBundles](https://github.com/xplshn/pelf/), [FlatImages](https://github.com/ruanformigoni/flatimage) and [RunImages](https://github.com/VHSgunzo). These did not fit what Toolpacks was, so **pkgcache** was created on **2024-09-25** to hold them, alongside **bincache** for static binaries.

Encouraged by community interest on [Lobsters](https://lobste.rs/s/iqxjee/poor_man_s_package_manager_only), [**@Azathothas**](https://github.com/Azathothas) approached [**@QaidVoid**](https://github.com/QaidVoid), and [Soar](https://github.com/pkgforge/soar) received its first commit on **2024-10-03**. The [PkgForge](https://github.com/pkgforge) organization was created on **2024-11-04**, and [soarpkgs](https://github.com/pkgforge/soarpkgs) with it.

## soarpkgs today

soarpkgs started as a tree of SBUILD recipes, YAML build scripts that produced the packages published through bincache and pkgcache. That arrangement is gone. The two caches were folded into a single index, and SBUILD was replaced by a [declarative format](../../packaging/) where a package is a pinned URL and a hash rather than a script that runs.

The few packages that genuinely need building moved to [pkgforge/builds](../../packaging/builds.md), which publishes releases soarpkgs pins like any other upstream.

## Inspiration

This project builds on the work of [andrew-d/static-binaries](https://github.com/andrew-d/static-binaries), [minos-org/minos-static](https://github.com/minos-org/minos-static), [mosajjal/binary-tools](https://github.com/mosajjal/binary-tools), [ryanwoodsmall/static-binaries](https://github.com/ryanwoodsmall/static-binaries), and others.

## Further reading

* [Static Linking Considered Harmful Considered Harmful](https://gavinhoward.com/2021/10/static-linking-considered-harmful-considered-harmful/)
* [Oasis Linux](https://github.com/oasislinux/oasis)
* [Stalix](https://stal-ix.github.io/STALIX.html)
