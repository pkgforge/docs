---
icon: hammer
description: Where the exceptions get built
---

# Builds

[pkgforge/builds](https://github.com/pkgforge/builds) builds the handful of packages that cannot be pinned straight from an upstream release, and publishes them as ordinary GitHub releases. [soarpkgs](../repositories/soarpkgs/) then pins those releases the same way it pins anyone else's, with a URL and a hash reviewed in a commit.

From soarpkgs' point of view this repository is just another upstream, which is the whole idea. soarpkgs stays declarative and nothing in it executes.

## When a package ends up here

Only when pinning upstream directly is impossible. The recurring cases are upstream shipping glibc-linked binaries, shipping only some architectures, or publishing no releases at all. Every build definition carries a `reason` field saying which case it is, because pinning upstream is always preferable where it exists.

```toml
reason = "upstream ships gnu-linked binaries only; soar needs static musl"
```

## Reproducibility

A built artifact has no external referent. Nobody else publishes those bytes, so the hash attests to our build rather than to something a third party can check. Reproducibility is what converts that back into something verifiable: if an independent rebuild produces the same hash, the builder stops being a single point of failure.

Every build therefore fixes what would otherwise vary between runs:

* source pinned by commit, never by tag, and verified after fetch
* toolchain pinned by image digest, never by tag
* `SOURCE_DATE_EPOCH` taken from the source commit, not the clock
* a fixed build path, since absolute paths leak into debug info
* `LC_ALL=C` and `TZ=UTC`
* a normalised archive: fixed mtime, uid and gid 0, sorted entries, and gzip's own header timestamp pinned to 0

A scheduled job rebuilds published packages and compares against the bytes in the release, so a definition that stops reproducing surfaces there rather than with whoever tries to verify it later.

{% hint style="warning" %}
Build dependencies are installed with `apk` or `apt` at build time and are not version pinned, so a distribution package update can still change the result. Closing that gap means building and pinning our own base image. Until then, reproducibility holds within a window rather than indefinitely.
{% endhint %}

## What gets checked before publishing

Compiling is not evidence that the result works, least of all when building for an architecture the builder cannot run. Every staged binary is checked:

* it is an ELF for the architecture it claims to be
* it has no `PT_INTERP`, so it is statically linked and needs no libc on the host
* it runs, under `qemu-user` when the build host is a different architecture

The last is opt-in per package, since not every binary has a harmless flag to invoke. A binary that is dynamically linked, built for the wrong machine, or unable to start fails the build rather than reaching a release.

## Who follows whom

For a package served partly from here, soarpkgs takes its version from our release rather than from upstream. Otherwise the two repositories race: soarpkgs resolves upstream's newest version, writes a URL pointing at a release here that does not exist yet, and its update fails until we catch up.

```toml
[update]
strategy   = "github-releases"
repo       = "pkgforge/builds"
tag-prefix = "nushell-"
```

The cost is that these packages reach soarpkgs only once built here. `[pkg] src` keeps pointing at the real upstream, so provenance does not move with the version.

## Architectures

A package is built only for the architectures upstream does not already serve. Where upstream publishes a static musl binary, soarpkgs pins that directly and this repository stays out of it.

x86_64 and aarch64 build natively on their own runners. riscv64 has no runner and no official Rust image, so it cross compiles through [cargo-zigbuild](https://github.com/rust-cross/cargo-zigbuild), which supplies a C cross toolchain for every target that plain `rustup target add` does not. Go cross compiles on its own with `CGO_ENABLED=0`.
