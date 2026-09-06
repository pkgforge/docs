---
icon: compact-disc
description: https://github.com/xplshn/pelf
---

# AppBundle

* **Author**: [`@xplshn`](https://github.com/xplshn)
* **Project Page**: [https://github.com/xplshn/pelf](https://github.com/xplshn/pelf)
* **Format Docs**: [https://xplshn.github.io/pelf/docs](https://xplshn.github.io/pelf/docs)
* **Prebuilts**: [AppBundleHUB](https://github.com/xplshn/AppBundleHUB), and [dbin](https://github.com/xplshn/dbin) as a package manager for them

AppBundles use the same AppDir layout AppImages do, so unpacking an AppImage and repacking it as an AppBundle is straightforward, and the runtime accepts the `--appimage-*` flags to stay a drop-in replacement. What differs is underneath: the payload may be `squashfs` or `dwarfs`, and the tools needed to mount it are embedded in the bundle rather than expected from the host.

The format does not insist on AppDir compliance, which is why it gets used for things an AppImage would not carry, such as whole toolchains or a window manager and its utilities in one file.

***

### In soarpkgs

{% hint style="info" %}
Soar installs this format from a [repository](../../../repositories/external/), a URL, or a local file, and a [recipe](../../../packaging/recipe.md) can name it as its `type`. No package in soarpkgs happens to use it at the moment.
{% endhint %}

***

### **Prerequisites (`HOST)`**

{% hint style="info" %}
* [**Fuse**](../errors-and-quirks/fuse.md): used to mount the payload. The `squashfs` and `dwarfs` tools are embedded in the bundle, so there is nothing to install for them. Where FUSE is unavailable, the `--appimage-extract-and-run` fallback applies, as it does for an AppImage.
* [**Fonts**](../errors-and-quirks/fonts.md): required to display/render non-English characters, symbols and emoji.
* [<mark style="color:blue;">**Kernel user namespaces**</mark>](../errors-and-quirks/namespaces.md): only for bundles that sandbox, such as those built by `pelfCreator` around an Alpine rootfs and bubblewrap.
{% endhint %}

***

### Quirks

{% hint style="info" %}
<mark style="color:red;">**WARNINGS**</mark>

* NEVER run **`strip`**, **`objcopy`** or any other binary rewriting tool as they will often just strip the **`squashfs|dwarfs`** archive, only preserving the **`runtime`**.
* A typical <mark style="color:green;">**`.appbundle`**</mark> file is not a real elf binary, thus will not survive this process.
* The filesystem is part of the name: a bundle is built as <mark style="color:green;">**`.dwfs.AppBundle`**</mark> or <mark style="color:green;">**`.sqfs.AppBundle`**</mark>. A DwarFS one needs a thumbnailer that understands DwarFS, the same as a DwarFS [AppImage](../appimage/) does.
* Mount directories carry the bundle's own id, so it is always clear which bundle a mount belongs to.
{% endhint %}
