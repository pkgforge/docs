---
icon: compact-disc
description: AppImages created from NixOs Derivations & FHS
---

# NixAppImage

* **Author**: [`@ralismark`](https://github.com/ralismark) `+` [`@Azathothas`](https://github.com/Azathothas) `+` [`Others`](https://github.com/NixOS/bundlers)
* **Project Page**: [https://github.com/pkgforge/nix-appimage](https://github.com/pkgforge/nix-appimage)
* Described as An AppImage created using a [Nix-Bundler](https://github.com/NixOS/bundlers) like [pkgforge/nix-appimage](https://github.com/pkgforge/nix-appimage) & [DavHau/nix-portable](https://github.com/DavHau/nix-portable)

***

### Schema

{% hint style="info" %}
[<mark style="color:purple;">**`.pkg`**</mark>](../../../sbuild/specification/2.pkg.md): <mark style="color:orange;">**`${PKG_NAME}`**</mark>

[<mark style="color:purple;">**`.pkg_type`**</mark>](../../../sbuild/specification/2.pkg.md): <mark style="color:green;">**`niximage`**</mark>

<mark style="color:blue;">**`${SBUILD_PKG}`**</mark> : <mark style="color:green;">**`${PKG_NAME}.nixappimage`**</mark>
{% endhint %}

***

### **Prerequisites (`HOST)`**

{% hint style="info" %}
* [**Fuse**](../errors-and-quirks/fuse.md): Required for mounting Filesystems & Images
* [**Fonts**](../errors-and-quirks/fonts.md): Required to display/render Non-English Chars, Emojis, Symbols etc.
* [<mark style="color:blue;">**Kernel User NameSpaces**</mark>](../errors-and-quirks/namespaces.md): Required for Sandboxing, Security & Performance
{% endhint %}

***

### Quirks

{% hint style="info" %}
<mark style="color:red;">**KNOWN ISSUES**</mark>

* **LibGL**: [https://github.com/NixOS/nixpkgs/issues/9415](https://github.com/NixOS/nixpkgs/issues/9415)
* **Size**: About **`2-5x`** larger than other formats, but **guarantee absolute portability**.

<mark style="color:red;">**WARNINGS**</mark>

* NEVER run **`strip`**, **`objcopy`** or any other binary rewriting tool as they will often just strip the **`squashfs|dwarfs`** archive, only preserving the **`runtime`**.
* A typical <mark style="color:green;">**`.nixappimage`**</mark> file is not a real elf binary, thus will not survive this process.
{% endhint %}
