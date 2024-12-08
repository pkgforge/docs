---
icon: boxes-packing
description: Supported HOST ($ARCH-$OS) , Type, & Total Number of Packages
---

# Packages

{% hint style="warning" %}
The following Caveats were applied:

* [x] Must NOT be [**associated with a mainstream distro**](#user-content-fn-1)[^1] (Excluded: [AUR](https://wiki.archlinux.org/title/Arch_User_Repository), [GURU](https://wiki.gentoo.org/wiki/Project:GURU), [NUR](https://nur.nix-community.org/) etc)
* [x] Must have an active development i.e **no abandonware**
* [x] We included the top 4 (5) Projects that met the above critera & had the most number of packages
{% endhint %}

***

### Host

{% hint style="info" %}
<mark style="color:blue;">**`AnyLinux`**</mark> == [<mark style="color:orange;">**`Any Distro`**</mark>](https://en.wikipedia.org/wiki/List_of_Linux_distributions)
{% endhint %}

<table><thead><tr><th width="183">Package Manager</th><th width="307">Supported OS</th><th>Supported Arch</th></tr></thead><tbody><tr><td><a href="https://github.com/ivan-hc/AM/tree/main/programs"><strong>AM</strong></a></td><td><a href="https://github.com/ivan-hc/AM#installation">AnyLinux</a></td><td><a href="https://github.com/ivan-hc/AM/blob/main/programs/aarch64-apps">aarch64</a>, <a href="https://github.com/ivan-hc/AM/blob/main/programs/i686-apps">i686</a>, <a href="https://github.com/ivan-hc/AM/blob/main/programs/x86_64-apps">x86_64</a></td></tr><tr><td><a href="https://brew.sh/"><strong>Brew</strong></a></td><td><a href="https://docs.brew.sh/Installation">macOS</a>, <a href="https://docs.brew.sh/Installation">AnyLinux</a></td><td><a href="https://docs.brew.sh/Installation">aarch64</a>, <a href="https://docs.brew.sh/Installation">x86_64</a></td></tr><tr><td><a href="https://github.com/pacstall"><strong>Pacstall</strong></a></td><td><a href="https://github.com/pacstall/pacstall#installing">Linux (Debian based Only)</a></td><td><a href="https://github.com/pacstall/pacstall#installing">All Debian Ports</a></td></tr><tr><td><a href="https://github.com/leleliu008/ppkg"><strong>PPKG</strong></a></td><td><a href="https://github.com/leleliu008/ppkg">FreeBSD</a>, <a href="https://github.com/leleliu008/ppkg">AnyLinux</a>, <a href="https://github.com/leleliu008/ppkg">MacOS</a>, <a href="https://github.com/leleliu008/ppkg">OpenBSD</a>, <a href="https://github.com/leleliu008/ppkg">NetBSD</a></td><td><a href="https://github.com/leleliu008/ppkg">aarch64</a>, <a href="https://github.com/leleliu008/ppkg">ppc64le</a>, <a href="https://github.com/leleliu008/ppkg">riscv64</a>, <a href="https://github.com/leleliu008/ppkg">s390x</a>, <a href="https://github.com/leleliu008/ppkg">x86_64</a></td></tr><tr><td><a href="https://github.com/pkgforge/soar"><strong>Soar</strong></a></td><td><a href="https://docs.pkgforge.dev/sbuild/specification/20.x_exec#os">Linux (For Now)</a></td><td><a href="https://docs.pkgforge.dev/sbuild/specification/20.x_exec#arch">aarch64</a>, <a href="https://docs.pkgforge.dev/sbuild/specification/20.x_exec#arch">arm64</a></td></tr></tbody></table>

***

### Types



***

### Total

<table data-full-width="false"><thead><tr><th width="97" data-type="number">AM</th><th width="93">Brew</th><th width="99">Pacstall</th><th width="79">PPKG</th><th>PkgForge (Soar)</th></tr></thead><tbody><tr><td>2613</td><td>7256</td><td>658</td><td>995</td><td>4748</td></tr></tbody></table>

[^1]: We allowed [Pacstall](https://github.com/pacstall/pacstall), as it's a community project & NOT backed by any distro. We could have included the [NUR](https://github.com/nix-community/NUR) too, but we already have [homebrew](https://brew.sh/) for reality checks...
