---
icon: compact-disc
description: A hybrid of Flatpak sandboxing with AppImage portability
---

# FlatImage

* Author: [`@ruanformigoni`](https://github.com/ruanformigoni)
* Project Page: [https://github.com/ruanformigoni/flatimage](https://github.com/ruanformigoni/flatimage)
* Detailed Docs: [https://flatimage.github.io/docs/](https://flatimage.github.io/docs/)

***

### In soarpkgs

{% hint style="info" %}
Soar installs this format from a [repository](../../../repositories/external/), a URL, or a local file, and a [recipe](../../../packaging/recipe.md) can name it as its `type`. No package in soarpkgs happens to use it at the moment.
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
