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

What an AppImage needs from the host depends on which kind of AppImage it is.

{% hint style="success" %}
<mark style="color:green;">**Anylinux AppImages**</mark>

Effectively nothing. The [uruntime](https://github.com/VHSgunzo/uruntime) they ship mounts with FUSE where `fusermount` is available, falls back to [user namespaces](../errors-and-quirks/namespaces.md) where it is not, and falls back again to extracting into `TMPDIR` and running from there. There is no <mark style="color:orange;">**`libfuse2`**</mark> to install, no FHS layout to satisfy, and no dependency on the host libc, since the libraries travel with the image.

[**Fonts**](../errors-and-quirks/fonts.md) are still the host's, so non-English characters, symbols and emoji need them installed.
{% endhint %}

{% hint style="info" %}
<mark style="color:orange;">**Traditional AppImages**</mark>

One built with `linuxdeploy` or a similar tool asks for more: [**FUSE**](../errors-and-quirks/fuse.md) to mount itself, an FHS-compliant system, and a glibc no older than the one it was built against. Where FUSE is unavailable you have to extract it yourself, with [<mark style="color:orange;">`--appimage-extract-and-run`</mark> | <mark style="color:orange;">`APPIMAGE_EXTRACT_AND_RUN=1`</mark>](https://docs.appimage.org/user-guide/troubleshooting/fuse.html#fallback-if-fuse-can-t-be-made-working).
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
{% endhint %}

{% hint style="warning" %}
<mark style="color:purple;">**NixOS**</mark>

Do not run an Anylinux AppImage through <mark style="color:orange;">**`appimage-run`**</mark>. It mounts the image itself instead of letting the image run itself, and it expects SquashFS, so a DwarFS one fails with `ERROR: Can't find a valid SQUASHFS superblock`. These need no FHS wrapper on NixOS, so disabling `appimage-run` is the whole fix.

The [NixOS wiki page](https://wiki.nixos.org/wiki/Appimage) applies to the older SquashFS kind, which genuinely does need an FHS environment and host libraries.
{% endhint %}

{% hint style="info" %}
<mark style="color:blue;">**Thumbnails**</mark>

A DwarFS AppImage needs a thumbnailer that understands DwarFS. [appimage-thumbnailer](https://github.com/kem-a/appimage-thumbnailer) and [simple-appimage-thumbnailer](https://github.com/Samueru-sama/simple-appimage-thumbnailer) both do.
{% endhint %}
