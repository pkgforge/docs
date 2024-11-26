---
icon: block-question
description: How to request a new Package
---

# Package-Request

{% hint style="info" %}
* This is **only for packages that have been selected & marked** as<mark style="color:orange;">**`.pkgcache`**</mark> at [**SoarPkgs (pkgforge-community)**](https://github.com/pkgforge/soarpkgs/blob/main/README.md)
{% endhint %}

***

### Criteria

{% hint style="info" %}
Exceptions Apply, [**Discussion**](https://github.com/pkgforge/pkgcache/issues) is encouraged
{% endhint %}

* [x] Must already exist as a [<mark style="color:purple;">**`.SBUILD`**</mark>](broken-reference)at [**SoarPkgs (pkgforge-community)**](https://github.com/pkgforge/soarpkgs/blob/main/README.md)
* [x] Must be **Portable**, i.e. must work on all **Libc** ([GLIBC](https://www.gnu.org/software/libc/), [MUSL](https://musl.libc.org/) etc) **Linux Distros**
* [x] Must have **an entry on** [**RepoLogy**](https://repology.org/projects/)
* [x] Must have **received an update** within the **last 6 Month** or, at the very extent, within the **last 12 Month**.
* [x] If on [**GitHub**](https://github.com/) & Official, then it must have at least **100 Stars,** or otherwise be a well known package
* [x] Optionally, also already exist at [https://flathub.org/](https://flathub.org/), tho this is not a hard requirement.

### Guide

{% hint style="info" %}
This repository prefers quality over quantity, so some strict rules & guidelines have to be followed

* Check yor requested package meets the [Criteria listed above](https://docs.pkgforge.dev/orgs/pkgforge-core/projects/pkgcache/package-request#criteria), if you would like to argue, do it: [https://github.com/pkgforge/pkgcache/issues](https://github.com/pkgforge/pkgcache/issues)
* Also make sure you **do not request an already existing package**
* Check using [<mark style="color:orange;">**soar**</mark>](https://soar.qaidvoid.dev/search)

```bash
soar search "${PKG_NAME}#pkg"
```

* If you want to see the list: [<mark style="color:purple;">**aarch64-Linux**</mark>](https://github.com/pkgforge/pkgcache/tree/main/aarch64-Linux) [<mark style="color:purple;">**x86\_64-Linux**</mark>](https://github.com/pkgforge/pkgcache/tree/main/x86_64-Linux)
{% endhint %}

* [x] Find the Package's <mark style="color:purple;">**`.SBUILD`**</mark> from [https://github.com/pkgforge/soarpkgs/tree/main/packages](https://github.com/pkgforge/soarpkgs/tree/main/packages)

{% hint style="info" %}
1. [Create an Issue](https://github.com/pkgforge/soarpkgs/issues/new/choose): [https://github.com/pkgforge/soarpkgs/issues/new/choose](https://github.com/pkgforge/soarpkgs/issues/new/choose) `>>` [**Prebuilt Request (Generic)**](https://github.com/pkgforge/soarpkgs/issues/new?assignees=Azathothas\&labels=pkgcache\&projects=\&template=prebuilt-request--generic-.md\&title=%5BPkgCache+Request%5D+NAME_OF_PKG)
2. Replace with actual values; **Title**: **\[PkgCache Request] NAME\_OF\_PKG**
3. Body: Fill with correct/Relevant Values from the Information you gathered
4. Wait for one of the maintainers to respond
{% endhint %}
