---
icon: message-question
description: Frequently asked questions
---

# FAQ

### Is this an AUR?

It borrows the idea of a community tree of package definitions, but not the model. AUR recipes build on your machine; soarpkgs never builds anything on yours, and nothing in the tree executes at all. A package is a URL and a hash, reviewed in a pull request before it is merged.

***

### Are there other repositories I should add?

No. soarpkgs is the only repository PkgForge publishes, and it is enabled by default, so there is nothing extra to add.

Soar itself is not tied to it. If you find a third party repository, or want to [run your own](../external/), Soar will happily use it.

***

### What happened to bincache and pkgcache?

They were the two prebuilt caches soarpkgs generated metadata for, one for static binaries and one for GUI applications. Both are gone. soarpkgs now publishes a single index per host, and the distinction between the two lives in the package's `type` field instead.

***

### What happened to SBUILD?

It was retired along with the caches. SBUILD was a YAML build script, and a package's hash was whatever the build happened to produce. Packages are now [declared in TOML](../../packaging/), pinning upstream's own release artifact by hash. See [packaging](../../packaging/) for the format that replaced it.

***

### Where do packages actually come from?

Nearly all of them come straight from an upstream release: the recipe names the asset and pins its hash. The exceptions are built in [pkgforge/builds](../../packaging/builds.md), which publishes ordinary GitHub releases that soarpkgs then pins like anyone else's.

A package is built there only when pinning upstream is impossible, usually because upstream ships glibc-linked binaries, serves only some architectures, or publishes no releases at all.

***

### glibc or musl?

Static packages are musl-linked wherever upstream offers the choice, since a glibc-linked binary is not portable across distributions in the way this whole project depends on. Where we build a package ourselves, musl is required rather than preferred, and a dynamically linked result fails the build.

***

### Which architectures are supported?

`x86_64-linux`, `aarch64-linux` and `riscv64-linux`. Whether a given package serves all three depends on what upstream ships, and riscv64 in particular is thinner than the other two.

***

### How do I know a download was not tampered with?

The index is signed with minisign, and every artifact carries a blake3 hash that was committed and reviewed. Soar checks both, and independently, so a validly signed index carrying a wrong hash still fails at install. See [security](security.md).

***

### Where did all this come from?

See [history](../../orgs/pkgforge-core/history.md).
