---
icon: compact-disc
description: Portable single-file Linux container, Similar to FlatImage
---

# RunImage (TBD)

* **Author**: [`@VHSgunzo`](https://github.com/VHSgunzo)
* **Project Page**: [https://github.com/VHSgunzo/runimage](https://github.com/VHSgunzo/runimage)

***

### Schema

{% hint style="info" %}
[<mark style="color:purple;">**`.pkg`**</mark>](../../../sbuild/specification/2.pkg.md): <mark style="color:orange;">**`${PKG_NAME}`**</mark>

[<mark style="color:purple;">**`.pkg_type`**</mark>](../../../sbuild/specification/2.pkg.md): <mark style="color:green;">**`runimage`**</mark>

<mark style="color:blue;">**`${SBUILD_PKG}`**</mark> : <mark style="color:green;">**`${PKG_NAME}.runimage`**</mark>
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
<mark style="color:red;">**WARNINGS**</mark>

* NEVER run **`strip`**, **`objcopy`** or any other binary rewriting tool as they will often just strip the **`squashfs|dwarfs`** archive, only preserving the **`runtime`**.
* A typical <mark style="color:green;">**`.runimage`**</mark> file is not a real elf binary, thus will not survive this process.
{% endhint %}
