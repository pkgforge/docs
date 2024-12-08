---
icon: boxes-packing
description: Supported HOST ($ARCH-$OS) , Type, & Total Number of Packages
---

# 3. Packages

### Host

{% hint style="info" %}
<mark style="color:blue;">**`AnyLinux`**</mark> == [<mark style="color:orange;">**`Any Distro`**</mark>](https://en.wikipedia.org/wiki/List_of_Linux_distributions)
{% endhint %}

<table><thead><tr><th width="183">Package Manager</th><th width="307">Supported OS</th><th>Supported Arch</th></tr></thead><tbody><tr><td><a href="https://github.com/ivan-hc/AM/tree/main/programs"><mark style="color:purple;"><strong><code>AM</code></strong></mark></a></td><td><a href="https://github.com/ivan-hc/AM#installation">AnyLinux</a></td><td><a href="https://github.com/ivan-hc/AM/blob/main/programs/aarch64-apps">aarch64</a>, <a href="https://github.com/ivan-hc/AM/blob/main/programs/i686-apps">i686</a>, <a href="https://github.com/ivan-hc/AM/blob/main/programs/x86_64-apps">x86_64</a></td></tr><tr><td><a href="https://brew.sh/"><mark style="color:purple;"><strong><code>Brew</code></strong></mark></a></td><td><a href="https://docs.brew.sh/Installation">macOS</a>, <a href="https://docs.brew.sh/Installation">AnyLinux</a></td><td><a href="https://docs.brew.sh/Installation">aarch64</a>, <a href="https://docs.brew.sh/Installation">x86_64</a></td></tr><tr><td><a href="https://github.com/pacstall"><mark style="color:purple;"><strong><code>Pacstall</code></strong></mark></a></td><td><a href="https://github.com/pacstall/pacstall#installing">Linux (Debian based Only)</a></td><td><a href="https://github.com/pacstall/pacstall#installing">All Debian Ports</a></td></tr><tr><td><a href="https://github.com/leleliu008/ppkg"><mark style="color:purple;"><strong><code>PPKG</code></strong></mark></a></td><td><a href="https://github.com/leleliu008/ppkg">FreeBSD</a>, <a href="https://github.com/leleliu008/ppkg">AnyLinux</a>, <a href="https://github.com/leleliu008/ppkg">MacOS</a>, <a href="https://github.com/leleliu008/ppkg">OpenBSD</a>, <a href="https://github.com/leleliu008/ppkg">NetBSD</a></td><td><a href="https://github.com/leleliu008/ppkg">aarch64</a>, <a href="https://github.com/leleliu008/ppkg">ppc64le</a>, <a href="https://github.com/leleliu008/ppkg">riscv64</a>, <a href="https://github.com/leleliu008/ppkg">s390x</a>, <a href="https://github.com/leleliu008/ppkg">x86_64</a></td></tr><tr><td><a href="https://github.com/pkgforge/soar"><mark style="color:purple;"><strong><code>Soar</code></strong></mark></a></td><td><a href="https://docs.pkgforge.dev/sbuild/specification/20.x_exec#os">AnyLinux (For Now)</a></td><td><a href="https://docs.pkgforge.dev/sbuild/specification/20.x_exec#arch">aarch64</a>, <a href="https://docs.pkgforge.dev/sbuild/specification/20.x_exec#arch">arm64</a></td></tr></tbody></table>

***

### Portability

{% hint style="success" %}
This specifies if any of the packages offered by the package managers are usable **standalone,** aka **without using the package manager** & **just using curl/wget** or **just downloading from the browser**.
{% endhint %}

| Package Manager                                                                                 | Is it Standalone?                                                        |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| [<mark style="color:purple;">**`AM`**</mark>](https://github.com/ivan-hc/AM/tree/main/programs) | [<mark style="color:orange;">**Sort of**</mark>](#user-content-fn-1)[^1] |
| [<mark style="color:purple;">**`Brew`**</mark>](https://brew.sh/)                               | [<mark style="color:red;">**No**</mark>](#user-content-fn-2)[^2]         |
| [<mark style="color:purple;">**`Pacstall`**</mark>](https://github.com/pacstall)                | [<mark style="color:red;">**No**</mark>](#user-content-fn-3)[^3]         |
| [<mark style="color:purple;">**`PPKG`**</mark>](https://github.com/leleliu008/ppkg)             | [<mark style="color:orange;">**Sort of**</mark>](#user-content-fn-4)[^4] |
| [<mark style="color:purple;">**`Soar`**</mark>](https://github.com/pkgforge/soar)               | [<mark style="color:green;">**Yes**</mark>](#user-content-fn-5)[^5]      |

***

### Prebuilt Cache

{% hint style="success" %}
This specifies if the **package repository** contain **prebuilds,** i.e. packages are **directly&#x20;**<mark style="color:green;">**downloadable**</mark>**&#x20;without&#x20;**<mark style="color:orange;">**building/fixing/patching**</mark>**&#x20;anything**.&#x20;
{% endhint %}

| Package Manager                                                                                 | Provides Prebuilts?                                                                                                                                                                                                 |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [<mark style="color:purple;">**`AM`**</mark>](https://github.com/ivan-hc/AM/tree/main/programs) | [<mark style="color:orange;">**N/A**</mark>](#user-content-fn-6)[^6]                                                                                                                                                |
| [<mark style="color:purple;">**`Brew`**</mark>](https://brew.sh/)                               | <mark style="color:green;">**Yes**</mark>, [Prebuilt Packages are offered as bottles](https://docs.brew.sh/FAQ#why-do-you-compile-everything)                                                                       |
| [<mark style="color:purple;">**`Pacstall`**</mark>](https://github.com/pacstall)                | [<mark style="color:red;">**No**</mark>](#user-content-fn-7)[^7]                                                                                                                                                    |
| [<mark style="color:purple;">**`PPKG`**</mark>](https://github.com/leleliu008/ppkg)             | [<mark style="color:red;">**No**</mark>](#user-content-fn-8)[^8]                                                                                                                                                    |
| [<mark style="color:purple;">**`Soar`**</mark>](https://github.com/pkgforge/soar)               | <mark style="color:green;">**Yes**</mark>, See our [**edge**](https://docs.pkgforge.dev/repositories/pkgforge-edge/infra) & [**stable**](https://docs.pkgforge.dev/repositories/pkgforge-stable/infra) Repositories |

***

### Types

{% hint style="warning" %}
* AM [uses pkforge's repos](https://github.com/ivan-hc/AM/blob/31b14299c7e255b852fbfc5aa7174a90b12a5b66/README.md?plain=1#L226) for most of its binary support, i.e. NOT its [own repository](https://github.com/ivan-hc/AM/tree/main/programs)
* AM has an open issue for supporting more formats: [https://github.com/ivan-hc/AM/issues/1099](https://github.com/ivan-hc/AM/issues/1099)
* Brew (Cask --> AppImage): [https://github.com/orgs/Homebrew/discussions/3789](https://github.com/orgs/Homebrew/discussions/3789)
* <mark style="color:green;">**`Full`**</mark>  --> **Support + Manage + Integration**
* <mark style="color:orange;">**`Limited`**</mark> --> **Support + Manage (Partial)**
* <mark style="color:red;">**`None`**</mark>  --> **No Support At All**
{% endhint %}

| Package Manager                                                                                 | Supported Types                                                                                                                                                                                                                                                                                                                                                                          |
| ----------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [<mark style="color:purple;">**`AM`**</mark>](https://github.com/ivan-hc/AM/tree/main/programs) | AppImage (<mark style="color:green;">**Full**</mark>), AppBundles (<mark style="color:green;">**Full**</mark>), Binaries (<mark style="color:orange;">**3rd Party**</mark>), [Libraries <mark style="color:red;">**(None)**</mark>](#user-content-fn-9)[^9]                                                                                                                              |
| [<mark style="color:purple;">**`Brew`**</mark>](https://brew.sh/)                               | Binaries (<mark style="color:green;">**Full**</mark>) , Libraries ([Limited](https://github.com/orgs/Homebrew/discussions/4647)), [AppImages & Others](../../formats/packages/) (<mark style="color:red;">**None**</mark>)                                                                                                                                                               |
| [<mark style="color:purple;">**`Pacstall`**</mark>](https://github.com/pacstall)                | Binaries (<mark style="color:green;">**Full**</mark>), Libraries (<mark style="color:green;">**Full**</mark>) , [AppImages & Others <mark style="color:orange;">(</mark><mark style="color:orange;">**Limited**</mark><mark style="color:orange;">)</mark>](https://github.com/pacstall/pacstall/wiki/FAQ#well-what-about-universal-packaging-methods-like-appimages-snaps-and-flatpaks) |
| [<mark style="color:purple;">**`PPKG`**</mark>](https://github.com/leleliu008/ppkg)             | Binaries (<mark style="color:green;">**Full**</mark>), Libraries (<mark style="color:orange;">**Limited**</mark>)                                                                                                                                                                                                                                                                        |
| [<mark style="color:purple;">**`Soar`**</mark>](https://github.com/pkgforge/soar)               | [Binaries](../../formats/binaries/) (<mark style="color:green;">**Full**</mark>) & All the [Zillion other Formats](../../formats/packages/) (<mark style="color:green;">**Full**</mark>), [Libraries <mark style="color:red;">**(None)**</mark>](#user-content-fn-10)[^10]                                                                                                               |

***

### Total

{% hint style="info" %}
The total number of packages (each recipe is counted individually) [auto updated](../../.github/workflows/healthchecks_housekeeping.yaml) every 2hrs
{% endhint %}

<table data-full-width="false"><thead><tr><th width="97">AM</th><th width="93">Brew</th><th width="99">Pacstall</th><th width="79">PPKG</th><th>PkgForge (Soar)</th></tr></thead><tbody><tr><td>2613</td><td>7256</td><td>658</td><td>995</td><td>4748</td></tr></tbody></table>

[^1]: Needs the cli to build & install. Installed packages need to be copied manually & then moved

[^2]: Needs the cli to build & install. Installed packages are not standalone

[^3]: Needs the cli to build & install. Installed packages are not standalone

[^4]: Needs to parse, & build the formula themselves. The generated bundle is standalone

[^5]: You can use any of our **`prebuilt`** packages just by downloading it & without using soar at all. \
    Even the [<mark style="color:purple;">**SBUILD**</mark>](https://github.com/pkgforge/soarpkgs) packages can be bundled with <mark style="color:orange;">`--bundle`</mark>

[^6]: AM mostly redownloads prebuilt packages from other sources. It has no prebuilt central cache. But We can't say NO, since it does download prebuilds, albeit from other sources.

[^7]: Builds & Installs from source. Not everything as it depends on their build recipe, but the majority is.

[^8]: Builds almost everything from source.\
    They do publish prebuilds as releases, but the pkg-manager itself doesn't use pre-builts.

[^9]: Not in the Project's Scope

[^10]: Not in the Project's Scope
