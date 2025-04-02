---
icon: compact-disc
description: https://github.com/xplshn/AppBundleHUB
---

# AppBundle

* **Author**: [`@xplshn`](https://github.com/xplshn)
* **Project Page**: [https://github.com/xplshn/pelf/](https://github.com/xplshn/pelf/)
* **Sources**: Mostly prebuilts from [https://github.com/xplshn/AppBundleHUB](https://github.com/xplshn/AppBundleHUB)

***

### Schema

{% hint style="info" %}
[<mark style="color:purple;">**`.pkg`**</mark>](../../../sbuild/specification/2.pkg.md): <mark style="color:orange;">**`${PKG_NAME}`**</mark>

[<mark style="color:purple;">**`.pkg_type`**</mark>](../../../sbuild/specification/2.pkg.md): <mark style="color:green;">**`appbundle`**</mark>

<mark style="color:blue;">**`${SBUILD_PKG}`**</mark> : <mark style="color:green;">**`${PKG_NAME}.appbundle`**</mark>
{% endhint %}

***

### **Prerequisites (`HOST)`**

{% hint style="info" %}
* [**Fuse**](../errors-and-quirks/fuse.md): Required for mounting Filesystems & Images
* [**Fonts**](../errors-and-quirks/fonts.md): Required to display/render Non-English Chars, Emojis, Symbols etc.
{% endhint %}

***

### Quirks

{% hint style="info" %}
* AppBundles will often have quirky filenames, such as .dwfs.AppBundle or .sqfs.AppBundle, this is in order to hint the user about the filesystem being used in the AppBundle. But this is just an arbitrary choice. The file can be named any way the user likes.

<mark style="color:red;">**WARNINGS**</mark>

* NEVER run **`strip`**, **`objcopy`** or any other binary rewriting tool as they will often just strip the **`squashfs|dwarfs`** archive, only preserving the **`runtime`**.
{% endhint %}
