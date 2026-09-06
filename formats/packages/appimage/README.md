---
icon: compact-disc
description: https://en.wikipedia.org/wiki/AppImage
---

# AppImage

{% hint style="info" %}
<mark style="color:purple;">**Sources**</mark>

* Upstream's own AppImage where it exists and is actively maintained
* Otherwise one built by [pkgforge-dev](../../../orgs/pkgforge-dev/), most often through [Anylinux-AppImages](../../../orgs/pkgforge-dev/projects/anylinux-appimages.md)
{% endhint %}

### In soarpkgs

{% hint style="info" %}
[`type`](../../../packaging/recipe.md) is <mark style="color:green;">**`appimage`**</mark>. The artifact is the package, so a recipe normally installs nothing out of it and the AppImage is simply pinned by URL and hash.
{% endhint %}

***

### **Prerequisites (`HOST)`**

{% hint style="info" %}
* [**Fuse**](../errors-and-quirks/fuse.md): Required for mounting Filesystems & Images (Can still be run with [<mark style="color:orange;">`--appimage-extract-and-run`</mark> | <mark style="color:orange;">`APPIMAGE_EXTRACT_AND_RUN=1`</mark>](https://docs.appimage.org/user-guide/troubleshooting/fuse.html#fallback-if-fuse-can-t-be-made-working))
* [**Fonts**](../errors-and-quirks/fonts.md): Required to display/render Non-English Chars, Emojis, Symbols etc.
* [<mark style="color:blue;">**Kernel User NameSpaces**</mark>](../errors-and-quirks/namespaces.md): Required for Sandboxing, Security & Performance
{% endhint %}

***

### Sandbox

{% hint style="danger" %}
AppImages have no built-in sandboxing. An AppImage you run has whatever access your user does.
{% endhint %}

{% hint style="info" %}
[**simple-appimage-sandbox**](https://github.com/Samueru-sama/simple-appimage-sandbox) wraps one in [bubblewrap](https://github.com/containers/bubblewrap) from POSIX shell, and is the one we would point you at.

[aisap](https://github.com/mgord9518/aisap) exists and does the same job, but is no longer actively maintained.
{% endhint %}

***

### Quirks

{% hint style="info" %}
<mark style="color:red;">**WARNINGS**</mark>

* NEVER run **`strip`**, **`objcopy`** or any other binary rewriting tool as they will often just strip the **`squashfs|dwarfs`** archive, only preserving the **`runtime`**.
* A typical <mark style="color:green;">**`.appimage`**</mark> file is not a real elf binary, thus will not survive this process.
* On [<mark style="color:purple;">**NixOS**</mark>](https://nixos.org/), you will need to follow: [https://wiki.nixos.org/wiki/Appimage](https://wiki.nixos.org/wiki/Appimage)
{% endhint %}
