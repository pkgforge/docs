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

<table><thead><tr><th width="183">Package Manager</th><th width="307">Supported OS</th><th>Supported Arch</th></tr></thead><tbody><tr><td><a href="https://github.com/ivan-hc/AM/tree/main/programs"><strong>AM</strong></a></td><td><a href="https://github.com/ivan-hc/AM#installation">AnyLinux</a></td><td><a href="https://github.com/ivan-hc/AM/blob/main/programs/aarch64-apps">aarch64</a>, <a href="https://github.com/ivan-hc/AM/blob/main/programs/i686-apps">i686</a>, <a href="https://github.com/ivan-hc/AM/blob/main/programs/x86_64-apps">x86_64</a></td></tr><tr><td><a href="https://brew.sh/"><strong>Brew</strong></a></td><td><a href="https://docs.brew.sh/Installation">macOS</a>, <a href="https://docs.brew.sh/Installation">AnyLinux</a></td><td><a href="https://docs.brew.sh/Installation">aarch64</a>, <a href="https://docs.brew.sh/Installation">x86_64</a></td></tr><tr><td><a href="https://github.com/pacstall"><strong>Pacstall</strong></a></td><td><a href="https://github.com/pacstall/pacstall#installing">Linux (Debian based Only)</a></td><td><a href="https://github.com/pacstall/pacstall#installing">All Debian Ports</a></td></tr><tr><td><a href="https://github.com/leleliu008/ppkg"><strong>PPKG</strong></a></td><td><a href="https://github.com/leleliu008/ppkg">FreeBSD</a>, <a href="https://github.com/leleliu008/ppkg">AnyLinux</a>, <a href="https://github.com/leleliu008/ppkg">MacOS</a>, <a href="https://github.com/leleliu008/ppkg">OpenBSD</a>, <a href="https://github.com/leleliu008/ppkg">NetBSD</a></td><td><a href="https://github.com/leleliu008/ppkg">aarch64</a>, <a href="https://github.com/leleliu008/ppkg">ppc64le</a>, <a href="https://github.com/leleliu008/ppkg">riscv64</a>, <a href="https://github.com/leleliu008/ppkg">s390x</a>, <a href="https://github.com/leleliu008/ppkg">x86_64</a></td></tr><tr><td><a href="https://github.com/pkgforge/soar"><strong>Soar</strong></a></td><td><a href="https://docs.pkgforge.dev/sbuild/specification/20.x_exec#os">AnyLinux (For Now)</a></td><td><a href="https://docs.pkgforge.dev/sbuild/specification/20.x_exec#arch">aarch64</a>, <a href="https://docs.pkgforge.dev/sbuild/specification/20.x_exec#arch">arm64</a></td></tr></tbody></table>

***

### Types

{% hint style="warning" %}
* AM [uses pkforge's repos](https://github.com/ivan-hc/AM/blob/31b14299c7e255b852fbfc5aa7174a90b12a5b66/README.md?plain=1#L226) for most of it's binary support i.e NOT it's [own repository](https://github.com/ivan-hc/AM/tree/main/programs)
* AM has an open issue for supporting more formats: [https://github.com/ivan-hc/AM/issues/1099](https://github.com/ivan-hc/AM/issues/1099)
* Brew (Cask --> AppImage): [https://github.com/orgs/Homebrew/discussions/3789](https://github.com/orgs/Homebrew/discussions/3789)
* <mark style="color:green;">**`Full`**</mark>  --> **Support + Manage + Integration**
* <mark style="color:orange;">**`Limited`**</mark> --> **Support + Manage (Partial)**
* <mark style="color:red;">**`None`**</mark><mark style="color:red;">**&#x20;**</mark> --> **No Support At All**
{% endhint %}

| Package Manager                                            | Supported Types                                                                                                                                                                                                                                                                                                                                                                          |
| ---------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [**AM**](https://github.com/ivan-hc/AM/tree/main/programs) | AppImage (<mark style="color:green;">**Full**</mark>), AppBundles (<mark style="color:green;">**Full**</mark>), Binaries (<mark style="color:orange;">**3rd Party**</mark>), [Libraries <mark style="color:red;">**(None)**</mark>](#user-content-fn-2)[^2]                                                                                                                              |
| [**Brew**](https://brew.sh/)                               | Binaries (<mark style="color:green;">**Full**</mark>) , Libraries ([Limited](https://github.com/orgs/Homebrew/discussions/4647)), [AppImages & Others](../../formats/packages/) (<mark style="color:red;">**None**</mark>)                                                                                                                                                               |
| [**Pacstall**](https://github.com/pacstall)                | Binaries (<mark style="color:green;">**Full**</mark>), Libraries (<mark style="color:green;">**Full**</mark>) , [AppImages & Others <mark style="color:orange;">(</mark><mark style="color:orange;">**Limited**</mark><mark style="color:orange;">)</mark>](https://github.com/pacstall/pacstall/wiki/FAQ#well-what-about-universal-packaging-methods-like-appimages-snaps-and-flatpaks) |
| [**PPKG**](https://github.com/leleliu008/ppkg)             | Binaries (<mark style="color:green;">**Full**</mark>), Libraries (<mark style="color:orange;">**Limited**</mark>)                                                                                                                                                                                                                                                                        |
| [**Soar**](https://github.com/pkgforge/soar)               | [Binaries](../../formats/binaries/) (<mark style="color:green;">**Full**</mark>) & All the [Zillion other Formats](../../formats/packages/) (<mark style="color:green;">**Full**</mark>), [Libraries <mark style="color:red;">**(None)**</mark>](#user-content-fn-3)[^3]                                                                                                                 |

***

***

### Total

<table data-full-width="false"><thead><tr><th width="97" data-type="number">AM</th><th width="93">Brew</th><th width="99">Pacstall</th><th width="79">PPKG</th><th>PkgForge (Soar)</th></tr></thead><tbody><tr><td>2613</td><td>7256</td><td>658</td><td>995</td><td>4748</td></tr></tbody></table>

[^1]: We allowed [Pacstall](https://github.com/pacstall/pacstall), as it's a community project & NOT backed by any distro. We could have included the [NUR](https://github.com/nix-community/NUR) too, but we already have [homebrew](https://brew.sh/) for reality checks...

[^2]: Not in the Project's Scope

[^3]: Not in the Project's Scope
