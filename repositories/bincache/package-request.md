---
icon: block-question
description: How to request a new Package to be added to the Cache
---

# Package-Request

### Criteria

{% hint style="warning" %}
Exceptions Apply, [**Discussion**](https://github.com/pkgforge/soarpkgs/discussions) is encouraged
{% endhint %}

* [x] Must already exist as a [**`.SBUILD`**](https://docs.pkgforge.dev/sbuild/introduction)at [**SoarPkgs (pkgforge-community)**](https://github.com/pkgforge/soarpkgs/blob/main/README.md)
* [x] Must be **Portable**, i.e. must work on all **Libc** ([GLIBC](https://www.gnu.org/software/libc/), [MUSL](https://musl.libc.org/) etc) **Linux Distros**
* [x] Must have **an entry on** [**RepoLogy**](https://repology.org/projects/)
* [x] The total age of the project must be at least `~ 1 month`
* [x] Must have **received an update** within the **last 6 Month** or, at the very extent, within the **last 12 Month**.
* [x] If on Github, must have at least `10 stars`
* [x] The project must have a permissive `license` that allows binary redistribution

***

### Guide

{% hint style="info" %}
This is <mark style="color:red;">**NOT FOR REQUESTING NEW PACKAGES**</mark>, see: [https://docs.pkgforge.dev/repositories/soarpkgs/package-request](https://docs.pkgforge.dev/repositories/soarpkgs/package-request)

* [x] Also make sure you **do not request an already existing package**
* [x] Check using [<mark style="color:orange;">**soar**</mark>](https://soar.qaidvoid.dev/search)

```bash
soar search "${PKG_NAME}"
```

* [x] Search it on **Index**: [https://pkgs.pkgforge.dev/](https://pkgs.pkgforge.dev/)
{% endhint %}

* [x] After you are really sure that it's not available, [Create a new issue](https://github.com/pkgforge/soarpkgs/issues/new?assignees=Azathothas\&labels=prebuilt-request\&projects=\&template=2-prebuilt-cache-request.yaml\&title=CacheReq%3A+name_of_the_package) at: [https://github.com/pkgforge/soarpkgs/issues/new/choose](https://github.com/pkgforge/soarpkgs/issues/new/choose) >> [**Prebuilt Package Request (Cache)**](https://github.com/pkgforge/soarpkgs/issues/new?assignees=Azathothas\&labels=prebuilt-request\&projects=\&template=2-prebuilt-cache-request.yaml\&title=CacheReq%3A+name_of_the_package)

{% hint style="warning" %}
Fill all the required fields, **If you don't put effort into requesting a tool/pkg to be added here, neither will we.**
{% endhint %}
