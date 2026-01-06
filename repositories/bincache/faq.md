---
icon: message-question
description: Frequently Asked Questions
---

# FAQ

### Supported Platforms

Currently supported:
- `x86_64-Linux`
- `aarch64-Linux`

We'd like to support more architectures (riscv64, BSDs) but resources are limited.

---

### History & Lore

[**@Azathothas**](https://docs.pkgforge.dev/orgs/pkgforge-core/people#azathothas) used to be a bug bounty hunter. Setting up pentesting environments on remote servers was frustratingly slow - tools like [reconftw](https://github.com/six2dez/reconftw) would install entire toolchains just to get a few binaries.

Around **July 2023**, he started maintaining scripts to fetch precompiled binaries. What began as wrappers around [eget](https://github.com/zyedidia/eget) grew into multiple repos, eventually consolidating into [Toolpacks](https://github.com/Azathothas/Toolpacks). Toolpacks was archived on `2025-01-01` as part of a [major rewrite](https://github.com/pkgforge/bincache/issues/1).

Special mentions:
- [**@pwnwriter**](https://github.com/pwnwriter) created [Hysp](https://github.com/pwnwriter/hysp), the first package manager for Toolpacks (`Nov 2023`)
- [**@Xplshn**](https://github.com/xplshn) created [bdl](https://github.com/xplshn/Handyscripts/blob/master/bdl) → [BigDL](https://github.com/xplshn/bigdl) → [Dbin](https://github.com/xplshn/dbin)

Encouraged by community interest on [Lobsters](https://lobste.rs/s/iqxjee/poor_man_s_package_manager_only), [**@Azathothas**](https://docs.pkgforge.dev/orgs/pkgforge-core/people#azathothas) approached [**@QaidVoid**](https://github.com/QaidVoid), and [Soar](https://github.com/pkgforge/soar) received its first commit on **Oct 3, 2024**. The [PkgForge](https://github.com/pkgforge) organization was created on **Nov 4, 2024**.

#### Inspiration

This project builds on the work of: [andrew-d/static-binaries](https://github.com/andrew-d/static-binaries), [minos-org/minos-static](https://github.com/minos-org/minos-static), [mosajjal/binary-tools](https://github.com/mosajjal/binary-tools), [ryanwoodsmall/static-binaries](https://github.com/ryanwoodsmall/static-binaries), and others.

#### Further Reading

- [Static Linking Considered Harmful Considered Harmful](https://gavinhoward.com/2021/10/static-linking-considered-harmful-considered-harmful/)
- [Oasis Linux](https://github.com/oasislinux/oasis)
- [Stalix](https://stal-ix.github.io/STALIX.html)
