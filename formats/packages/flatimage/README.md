---
icon: compact-disc
description: A hybrid of Flatpak sandboxing with AppImage portability
---

# FlatImage

* **Author**: [`@ruanformigoni`](https://github.com/ruanformigoni)
* **Project Page**: [https://github.com/flatimage/flatimage](https://github.com/flatimage/flatimage)
* **Detailed Docs**: [https://flatimage.github.io/docs](https://flatimage.github.io/docs)

A FlatImage is closer to a container than to a single packaged application. It carries a whole subsystem, Alpine with `apk` or Arch with `pacman`, and its configuration lives in reserved space inside the ELF itself, so permissions, environment and bindings can be changed after the fact without rebuilding.

The payload is DwarFS, decompressed on the fly, and the tools to bring it up are statically linked and embedded.

{% hint style="info" %}
The project moved from `ruanformigoni/flatimage` to its own [`flatimage`](https://github.com/flatimage) organization. The old URL still redirects.
{% endhint %}

***

### In soarpkgs

{% hint style="info" %}
Soar installs this format from a [repository](../../../repositories/external/), a URL, or a local file, and a [recipe](../../../packaging/recipe.md) can name it as its `type`. No package in soarpkgs happens to use it at the moment.
{% endhint %}

***

### **Prerequisites (`HOST)`**

{% hint style="info" %}
* [<mark style="color:blue;">**Kernel user namespaces**</mark>](../errors-and-quirks/namespaces.md): the real requirement. The container is brought up unprivileged, so without them there is nothing to run in.
* [**Fuse**](../errors-and-quirks/fuse.md): used to mount the DwarFS payload. The tools are embedded, so there is nothing to install.
* [**Fonts**](../errors-and-quirks/fonts.md): required to display/render non-English characters, symbols and emoji.
{% endhint %}

***

### Sandbox

{% hint style="success" %}
FlatImages sandbox by default, and the default is zero access. Permissions are granted explicitly:

```bash
./alpine.flatimage fim-perms add xorg,wayland,network,audio
```

See [fim-perms](https://flatimage.github.io/docs/cmd/perms/) for the full list.
{% endhint %}

***

### Quirks

{% hint style="info" %}
<mark style="color:red;">**WARNINGS**</mark>

* NEVER run **`strip`**, **`objcopy`** or any other binary rewriting tool as they will often just strip the **`squashfs|dwarfs`** archive, only preserving the **`runtime`**.
* A typical <mark style="color:green;">**`.flatimage`**</mark> file is not a real elf binary, thus will not survive this process.
* An application that works in another format may still need a permission granted here before it does anything visible, since nothing is allowed until it is asked for.
{% endhint %}
