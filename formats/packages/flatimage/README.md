---
icon: compact-disc
description: A hybrid of Flatpak sandboxing with AppImage portability
---

# FlatImage

* Author: [`@ruanformigoni`](https://github.com/ruanformigoni)
* Project Page: [https://github.com/ruanformigoni/flatimage](https://github.com/ruanformigoni/flatimage)
* Detailed Docs: [https://flatimage.github.io/docs/](https://flatimage.github.io/docs/)

***

### Schema

{% hint style="info" %}
[<mark style="color:purple;">**`.pkg`**</mark>](../../../sbuild/specification/2.pkg.md): <mark style="color:orange;">**`${PKG_NAME}-${BASE_DISTRO_IMAGE}`**</mark>

[<mark style="color:purple;">**`.pkg_type`**</mark>](../../../sbuild/specification/2.pkg.md): <mark style="color:green;">**`flatimage`**</mark>

<mark style="color:blue;">**`${SBUILD_PKG}`**</mark> : <mark style="color:green;">**`${PKG_NAME}-${BASE_DISTRO_IMAGE}.flatimage`**</mark>

{% code overflow="wrap" %}
```bash
!#Examples
firefox-alpine.FlatImage --> Created using alpine as base BaseImage/RootFS
steam-cachyos.FlatImage --> Created using CachyOs as BaseImage/RootFS
librewolf-alpine-nix.FlatImage --> Created using alpine as BaseImage/RootFS with Nix on top of it
```
{% endcode %}
{% endhint %}

***

### **Prerequisites (`HOST)`**

{% hint style="info" %}
* [**Fuse**](../errors-and-quirks/fuse.md): Required for mounting Filesystems & Images
* [**Fonts**](../errors-and-quirks/fonts.md): Required to display/render Non-English Chars, Emojis, Symbols etc.
* [<mark style="color:blue;">**Kernel User NameSpaces**</mark>](../errors-and-quirks/namespaces.md): Required for Sandboxing, Security & Performance
{% endhint %}

***

### Sandbox

{% hint style="success" %}
FlatImages have built-in sandboxing, check docs: [https://flatimage.github.io/docs/cmd/perms/](https://flatimage.github.io/docs/cmd/perms/)&#x20;
{% endhint %}

***

### Quirks

{% hint style="info" %}
<mark style="color:red;">**WARNINGS**</mark>

* NEVER run **`strip`**, **`objcopy`** or any other binary rewriting tool as they will often just strip the **`squashfs|dwarfs`** archive, only preserving the **`runtime`**.
* A typical <mark style="color:green;">**`.flatimage`**</mark> file is not a real elf binary, thus will not survive this process.
{% endhint %}
