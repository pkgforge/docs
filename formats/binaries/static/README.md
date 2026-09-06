---
icon: box
description: Statically linked binaries (type = static)
---

# Static

A static package is one ELF binary with no `PT_INTERP`, so it needs no libc on the host and runs on any distribution of the right architecture. It is the format to prefer whenever a program can be built as one.

{% hint style="success" %}
<mark style="color:purple;">**Sources**</mark>

* Nearly all of them come straight from an upstream release. The [recipe](../../../packaging/recipe.md) names the asset and pins its hash, and nothing is built.
* The rest are built in [pkgforge/builds](../../../packaging/builds.md), which publishes releases soarpkgs pins the same way. A package ends up there only when pinning upstream is impossible.
{% endhint %}

{% hint style="success" %}
<mark style="color:orange;">**Build profile**</mark>

For the packages we do build:

* [x] musl, and statically linked. A dynamically linked result fails the build.
* [x] Source pinned by commit, toolchain pinned by image digest
* [x] [LTO](https://gcc.gnu.org/wiki/LinkTimeOptimization) and [PIE](https://en.wikipedia.org/wiki/Position-independent_code) where the project supports them
* [x] Prefer [**`mimalloc`**](https://github.com/microsoft/mimalloc) over other musl allocators, since musl's own is slow enough to be noticeable ([<mark style="color:red;">not always</mark>](#user-content-fn-1)[^1])
{% endhint %}

{% hint style="info" %}
Every staged binary is checked before it is published: it is an ELF for the architecture it claims to be, it has no `PT_INTERP`, and it starts. Compiling is not evidence that the result works, least of all when building for an architecture the builder cannot run.
{% endhint %}

A binary that needs desktop integration, meaning a `.desktop` entry and an icon, is better shipped as an [AppImage](../../packages/appimage/) or [onelf](../../packages/onelf/) package.

[^1]: We have had reports of users hitting segfaults on old hardware.
