---
icon: block-question
description: How to request a new Package
---

# Package-Request

### Guide

{% hint style="info" %}
There's no strict rules, however if you put in **some effort**, it **will be Resolved Sooner**

* [x] Also make sure you **do not request an already existing package**
* [x] Check using [<mark style="color:orange;">**soar**</mark>](https://soar.qaidvoid.dev/search)

```bash
#The bin (main catalogue)
soar search "${BIN_NAME}#bin"

#The baseutil catalogue
soar search "${BIN_NAME}#base"
```

* [x] Search it on [**Github**](https://github.com/pkgforge/soarpkgs/tree/main/packages): [https://github.com/Azathothas/Toolpacks/tree/main/.github/scripts](https://github.com/Azathothas/Toolpacks/tree/main/.github/scripts)
* [x] [https://github.com/Azathothas/Toolpacks/blob/main/aarch64\_arm64\_Linux/DETAILED.md](https://github.com/Azathothas/Toolpacks/blob/main/aarch64_arm64_Linux/DETAILED.md)
* [x] Detailed List: [https://github.com/Azathothas/Toolpacks/blob/main/x86\_64\_Linux/DETAILED.md](https://github.com/Azathothas/Toolpacks/blob/main/x86_64_Linux/DETAILED.md)
{% endhint %}

* [x] After you are really sure that it's not available, Read [BUILD\_NOTES.md](https://github.com/Azathothas/Toolpacks/blob/main/Docs/BUILD_NOTES.md). This contains notes on compiling static binaries. However, if there's already a static binary that's released, you can [**just use soar to fetch it**](https://github.com/pkgforge/soar).
* [x] After you have successfully **`built/compiled/fetched`** a **static** binary, you must check that it's truly static : [**Tests**](https://github.com/Azathothas/Toolpacks/blob/main/Docs/BUILD_NOTES.md#tests)
* [x] After all this, finally describe & provide step-by-step instruction by [creating a new issue](https://github.com/Azathothas/Toolpacks/issues/new) Make sure to include **ALL Steps** (Including getting source code). Be as verbose as possible. Include output of **`file` | `ldd` | `readelf`**. Optionally, also test the binary with **`qemu-$ARCH-static`** or a minimal VM/Docker Image (Preferably alpine) to ensure that it really does work.
* [x] If you can not (don't know how to) compile, [**create a new issue**](https://github.com/Azathothas/Toolpacks/issues/new) with **links to the PKG/Tool's homepage/source-code along with a brief description on what it does.**

{% hint style="warning" %}
**If you don't put effort into requesting a tool/pkg to be added here, neither will we.**
{% endhint %}
