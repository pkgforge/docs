---
icon: compact-disc
description: Directories packed into self-contained executables
---

# onelf

* **Author**: [`@QaidVoid`](https://github.com/QaidVoid)
* **Project Page**: [https://github.com/QaidVoid/onelf](https://github.com/QaidVoid/onelf)
* **Docs**: [https://onelf.qaidvoid.dev](https://onelf.qaidvoid.dev)

onelf packs a directory into a single self-extracting ELF binary. The binary carries a trailing footer, a zstd-compressed manifest, and a compressed payload. Running it unpacks what it needs and executes the entry point.

It exists for the case a static binary cannot cover: a program that comes with its own libraries or data files, where upstream ships something dynamically linked and there is nothing to statically link instead.

***

### In soarpkgs

{% hint style="info" %}
[`type`](../../../packaging/recipe.md) is <mark style="color:green;">**`onelf`**</mark>. These are produced in [pkgforge/builds](../../../packaging/builds.md) and pinned in soarpkgs like any other release artifact.
{% endhint %}

***

### **Prerequisites (`HOST)`**

{% hint style="info" %}
* [**Fonts**](../errors-and-quirks/fonts.md): Required to display/render Non-English Chars, Emojis, Symbols etc.
{% endhint %}

No FUSE and no user namespaces. The payload is extracted rather than mounted, so the format has fewer host requirements than the image formats do.

***

### Quirks

{% hint style="info" %}
<mark style="color:red;">**WARNINGS**</mark>

* NEVER run **`strip`**, **`objcopy`** or any other binary rewriting tool. They rewrite the ELF and drop everything past it, which is where the manifest and payload live.
* Desktop entries and icons follow the `.onelf/` convention inside the payload, which is how Soar finds them for desktop integration.
{% endhint %}
