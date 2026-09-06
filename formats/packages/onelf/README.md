---
icon: compact-disc
description: Directories packed into self-contained executables
---

# onelf

* **Author**: [`@QaidVoid`](https://github.com/QaidVoid)
* **Project Page**: [https://github.com/QaidVoid/onelf](https://github.com/QaidVoid/onelf)
* **Docs**: [https://onelf.qaidvoid.dev](https://onelf.qaidvoid.dev)

onelf packs a directory into a single self-contained ELF executable. The file carries a trailing footer, a zstd-compressed manifest, and a compressed payload, with a static musl runtime stub at the front that knows how to bring the payload up.

It exists for the case a static binary cannot cover: a program that comes with its own libraries or data files, where upstream ships something dynamically linked and there is nothing to statically link instead.

***

### In soarpkgs

{% hint style="info" %}
[`type`](../../../packaging/recipe.md) is <mark style="color:green;">**`onelf`**</mark>. These are produced in [pkgforge/builds](../../../packaging/builds.md) and pinned in soarpkgs like any other release artifact.
{% endhint %}

***

### **Prerequisites (`HOST)`**

{% hint style="success" %}
Nothing in particular. The runtime tries a ladder of execution modes and uses the first one the host supports, so it adapts rather than requiring anything.

[**Fonts**](../errors-and-quirks/fonts.md) are still the host's, so non-English characters, symbols and emoji need them installed.
{% endhint %}

### Execution modes

```
memfd                 a static single binary, straight into an anonymous fd
userns + FUSE         private mount, invisible, torn down by the kernel
fusermount3 + FUSE    host-visible mount, still lazy
userns + tmpfs        extracted into a private tmpfs
runtime directory     extracted into a private per-user directory
persistent cache      only on request
```

Every rung but the last leaves nothing behind when the application exits. Mounting is preferred over extracting wherever the host allows it, since it decompresses blocks on demand and starts fast regardless of package size.

{% hint style="info" %}
The bottom rung is the one that makes the ladder work. A host with no `/dev/fuse`, no unprivileged [user namespaces](../errors-and-quirks/namespaces.md) and no `fusermount3` still has a writable runtime directory, so the package still runs.
{% endhint %}

The persistent cache is the exception, because it is the one mode that leaves something on disk. The runtime never falls into it on its own: it runs when the package was built with it, when `ONELF_CACHE=1` is set, or when it is asked for explicitly.

`ONELF_MODE` forces a particular rung, which is useful for narrowing down a problem. A forced mode that fails is an error rather than a fallback:

```bash
ONELF_MODE=fuse   ./myapp.onelf
ONELF_MODE=rundir ./myapp.onelf
```

See [execution modes](https://onelf.qaidvoid.dev/guide/execution-modes) for what each one requires and what it costs.

***

### Quirks

{% hint style="info" %}
<mark style="color:red;">**WARNINGS**</mark>

* NEVER run **`strip`**, **`objcopy`** or any other binary rewriting tool. They rewrite the ELF and drop everything past it, which is where the manifest and payload live.
* Desktop entries and icons follow the `.onelf/` convention inside the payload, which is how Soar finds them for desktop integration.
* On Ubuntu 23.10 and later, AppArmor restricts unprivileged user namespaces for binaries without an installed profile, which a downloaded file never has. Those hosts land on the `fusermount3` rung instead, which works the same way but leaves a mount visible to other processes.
{% endhint %}
