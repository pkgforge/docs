---
icon: compact-disc
description: https://en.wikipedia.org/wiki/AppImage
---

# AppImage

### Schema

{% hint style="info" %}
[<mark style="color:purple;">**`.pkg`**</mark>](../../sbuild/specification/2.pkg.md): <mark style="color:orange;">**`${PKG_NAME}`**</mark>

[<mark style="color:purple;">**`.pkg_type`**</mark>](../../sbuild/specification/2.pkg.md): <mark style="color:green;">**`appimage`**</mark>

<mark style="color:blue;">**`${SBUILD_PKG}`**</mark> : <mark style="color:green;">**`${PKG_NAME}.appimage`**</mark>
{% endhint %}

***

### **Prerequisites (`HOST)`**

{% hint style="info" %}
* [**Fuse**](errors-and-quirks/fuse.md): Required for mounting Filesystems & Images (Can still be run with [<mark style="color:orange;">`--appimage-extract-and-run`</mark> | <mark style="color:orange;">`APPIMAGE_EXTRACT_AND_RUN=1`</mark>](https://docs.appimage.org/user-guide/troubleshooting/fuse.html#fallback-if-fuse-can-t-be-made-working))
* [**Fonts**](errors-and-quirks/fonts.md): Required to display/render Non-English Chars, Emojis, Symbols etc.
* [<mark style="color:blue;">**Kernel User NameSpaces**</mark>](errors-and-quirks/namespaces.md): Required for Sandboxing, Security & Performance
{% endhint %}

***

### Quirks

{% hint style="info" %}
<mark style="color:red;">**WARNINGS**</mark>

* NEVER run **`strip`**, **`objcopy`** or any other binary rewriting tool as they will often just strip the **`squashfs|dwarfs`** archive, only preserving the **`runtime`**.
* A typical <mark style="color:green;">**`.appimage`**</mark> file is not a real elf binary, thus will not survive this process.
* On [<mark style="color:purple;">**NixOS**</mark>](https://nixos.org/), you will need to follow: [https://wiki.nixos.org/wiki/Appimage](https://wiki.nixos.org/wiki/Appimage)
{% endhint %}
