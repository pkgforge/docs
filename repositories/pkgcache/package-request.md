---
icon: block-question
description: How to request a new Package to be added to the Cache
---

# Package-Request

### Criteria

{% hint style="warning" %}
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
This is **NOT FOR REQUESTING NEW PACKAGES**, see: [https://docs.pkgforge.dev/repositories/soarpkgs/package-request](https://docs.pkgforge.dev/repositories/soarpkgs/package-request)&#x20;

* [x] Also make sure you **do not request an already existing package**
* [x] Check using [**soar**](https://soar.qaidvoid.dev/search)

```bash
soar search "${PKG_NAME}"
```

* [x] Search it on **Index**: [https://pkgs.pkgforge.dev/](https://pkgs.pkgforge.dev/)
* [x] After you are really sure that it's not available, [Create a new issue](https://github.com/pkgforge/soarpkgs/issues/new?assignees=Azathothas\&labels=prebuilt-request\&projects=\&template=2-prebuilt-cache-request.yaml\&title=CacheReq%3A+name_of_the_package) at: [https://github.com/pkgforge/soarpkgs/issues/new/choose](https://github.com/pkgforge/soarpkgs/issues/new/choose) >> [**Prebuilt Package Request (Cache)**](https://github.com/pkgforge/soarpkgs/issues/new?assignees=Azathothas\&labels=prebuilt-request\&projects=\&template=2-prebuilt-cache-request.yaml\&title=CacheReq%3A+name_of_the_package)
{% endhint %}

{% hint style="warning" %}
Fill all the required fields, **If you don't put effort into requesting a tool/pkg to be added here, neither will we.**
{% endhint %}
