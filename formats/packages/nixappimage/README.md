---
icon: compact-disc
description: AppImages built from Nix derivations
---

# NixAppImage

* **Author**: [`@ralismark`](https://github.com/ralismark), with [others](https://github.com/NixOS/bundlers)
* **Project Page**: [https://github.com/ralismark/nix-appimage](https://github.com/ralismark/nix-appimage)
* **Sources**: [nixpkgs](https://github.com/NixOS/nixpkgs)

An AppImage produced by a [Nix bundler](https://github.com/NixOS/bundlers) rather than assembled by hand. The derivation's full closure goes into the image, which is what makes it portable: every dependency is present by construction, with nothing taken from the host and no dependency on the host's glibc.

```bash
nix bundle --bundler github:ralismark/nix-appimage nixpkgs#hello
```

The result is a [type 2 AppImage](https://github.com/AppImage/AppImageSpec/blob/ce1910e6443357e3406a40d458f78ba3f34293b8/draft.md#type-2-image-format), a runtime concatenated with a SquashFS filesystem, so everything true of a traditional AppImage is true of this one too.

{% hint style="warning" %}
[`pkgforge/nix-appimage`](https://github.com/pkgforge/nix-appimage), our fork with bubblewrap and a universal AppRun, is archived. It was built for the pkgcache era and outlived it. Upstream is the live one.
{% endhint %}

***

### In soarpkgs

{% hint style="info" %}
Soar installs this format from a [repository](../../../repositories/external/), a URL, or a local file, and a [recipe](../../../packaging/recipe.md) can name it as its `type`. No package in soarpkgs happens to use it at the moment.
{% endhint %}

***

### **Prerequisites (`HOST)`**

{% hint style="info" %}
* [<mark style="color:blue;">**Kernel user namespaces**</mark>](../errors-and-quirks/namespaces.md): required, and not optional here. The bundle has to put the Nix store where the closure expects it, which is what namespaces are for. Available since Linux 3.8, but disabled on some systems for security reasons.
* [**Fuse**](../errors-and-quirks/fuse.md): to mount the SquashFS, with `--appimage-extract-and-run` as the fallback, as for any traditional [AppImage](../appimage/).
* [**Fonts**](../errors-and-quirks/fonts.md): required to display/render non-English characters, symbols and emoji.
{% endhint %}

***

### Quirks

{% hint style="info" %}
<mark style="color:red;">**KNOWN ISSUES**</mark>

* **OpenGL**: graphics drivers are the one thing a closure cannot bring with it, since they have to match the host, so GL applications generally do not run off NixOS without something like [nixGL](https://github.com/guibou/nixGL). See [nixpkgs#9415](https://github.com/NixOS/nixpkgs/issues/9415).
* **Desktop integration**: `.desktop` files and icons are copied on a best-effort basis, so an application may run fine and still not appear in a launcher.
* **Size**: roughly `2-5x` larger than the other formats, which is the cost of shipping the whole closure and the reason portability is otherwise absolute.
* Plain files in the root directory are not visible to the bundled application.

<mark style="color:red;">**WARNINGS**</mark>

* NEVER run **`strip`**, **`objcopy`** or any other binary rewriting tool as they will often just strip the **`squashfs`** archive, only preserving the **`runtime`**.
* A typical <mark style="color:green;">**`.nixappimage`**</mark> file is not a real elf binary, thus will not survive this process.
{% endhint %}
