---
icon: compact-disc
description: Portable single-file Linux container, similar to FlatImage
---

# RunImage

* **Author**: [`@VHSgunzo`](https://github.com/VHSgunzo)
* **Project Page**: [https://github.com/VHSgunzo/runimage](https://github.com/VHSgunzo/runimage)
* **Base**: an [Arch Linux rootfs](https://github.com/VHSgunzo/runimage-rootfs), with packages installed into it and the result repackaged

A RunImage is a single-file Linux container. It runs in unprivileged user namespaces, mounts a DwarFS or SquashFS payload through the [uruntime](https://github.com/VHSgunzo/uruntime), and does its containment with a statically compiled [bubblewrap](https://github.com/containers/bubblewrap). The binaries inside are static and wired up with [sharun](https://github.com/VHSgunzo/sharun), so nothing is taken from the host.

{% hint style="warning" %}
[`pkgforge-dev/runimage-base`](https://github.com/pkgforge-dev/runimage-base), which built the base images we used, is archived. Upstream's own rootfs is the live one.
{% endhint %}

***

### In soarpkgs

{% hint style="info" %}
Soar installs this format from a [repository](../../../repositories/external/), a URL, or a local file, and a [recipe](../../../packaging/recipe.md) can name it as its `type`. No package in soarpkgs happens to use it at the moment.
{% endhint %}

***

### **Prerequisites (`HOST)`**

{% hint style="info" %}
* [<mark style="color:blue;">**Kernel user namespaces**</mark>](../errors-and-quirks/namespaces.md): the real requirement, since the container is unprivileged. Kernel 5.0 or newer is recommended.
* [**Fuse**](../errors-and-quirks/fuse.md): preferred but not required. Without it the image runs unpacked, through `--runtime-extract-and-run` or `RUNTIME_EXTRACT_AND_RUN=1`.
* [**Fonts**](../errors-and-quirks/fonts.md): required to display/render non-English characters, symbols and emoji.
{% endhint %}

***

### Sandbox

{% hint style="success" %}
RunImages sandbox through bubblewrap, tuned with `RIM_UNSHARE_*` environment variables for the home directory, host processes and so on. See [usage](https://github.com/VHSgunzo/runimage#usage) for the full set.
{% endhint %}

***

### Quirks

{% hint style="info" %}
<mark style="color:red;">**WARNINGS**</mark>

* NEVER run **`strip`**, **`objcopy`** or any other binary rewriting tool as they will often just strip the **`squashfs|dwarfs`** archive, only preserving the **`runtime`**.
* A typical <mark style="color:green;">**`.runimage`**</mark> file is not a real elf binary, thus will not survive this process.
* A RunImage carries a distribution rather than an application, so it is considerably larger than the equivalent AppImage or static binary.
{% endhint %}
