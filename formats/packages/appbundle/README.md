---
icon: compact-disc
description: https://github.com/xplshn/AppBundleHUB
---

# AppBundle

* **Author**: [`@xplshn`](https://github.com/xplshn)
* **Project Page**: [https://github.com/xplshn/pelf/](https://github.com/xplshn/pelf/)

***

### Schema

{% hint style="info" %}
[<mark style="color:purple;">**`.pkg`**</mark>](../../../sbuild/specification/2.pkg.md): <mark style="color:orange;">**`${PKG_NAME}`**</mark>

[<mark style="color:purple;">**`.pkg_type`**</mark>](../../../sbuild/specification/2.pkg.md): <mark style="color:green;">**`appbundle`**</mark>

<mark style="color:blue;">**`${SBUILD_PKG}`**</mark> : <mark style="color:green;">**`${PKG_NAME}.appbundle`**</mark>
{% endhint %}

***

### Quirks

{% hint style="info" %}
<mark style="color:red;">**WARNINGS**</mark>

* NEVER run **`strip`**, **`objcopy`** or any other binary rewriting tool as they will often just strip the **`squashfs|dwarfs`** archive, only preserving the **`runtime`**.
* A typical <mark style="color:green;">**`.appimage`**</mark> file is not a real elf binary, thus will not survive this process.
{% endhint %}
