---
icon: shield-quartered
description: It is NEVER a good idea to install random packages from random sources.
---

# Security

{% hint style="success" %}
Recommended Reading:

* [x] [pkgforge-edge/security](../../orgs/pkgforge-security/)
{% endhint %}

Other than the details mentioned at [https://docs.pkgforge.dev/repositories/pkgforge-edge/security](https://docs.pkgforge.dev/repositories/pkgforge-edge/security), we follow some additional precautions for[ SoarPkgs](https://docs.pkgforge.dev/orgs/pkgforge-core/projects/soarpkgs):&#x20;

1. [PkgForge](https://github.com/pkgforge) maintains up-to-date [Forks](https://github.com/orgs/pkgforge-community/repositories?q=fork%3Atrue+archived%3Afalse) of all the <mark style="color:red;">**Unofficial**</mark> Packages that are added to [SoarPkgs](https://docs.pkgforge.dev/orgs/pkgforge-core/projects/soarpkgs) : [https://github.com/orgs/pkgforge-community/repositories?q=fork%3Atrue+archived%3Afalse](https://github.com/orgs/pkgforge-community/repositories?q=fork%3Atrue+archived%3Afalse)

{% hint style="info" %}
More details: [https://github.com/pkgforge-community#why-did-you-fork-my-repo](https://github.com/pkgforge-community#why-did-you-fork-my-repo)
{% endhint %}

2. These [Forks](https://github.com/orgs/pkgforge-community/repositories?q=fork%3Atrue+archived%3Afalse) ensure we have [Complete History of All Commits & All Releases](https://github.com/pkgforge-community/repo-data)
3. The [<mark style="color:purple;">`SBUILD`</mark>](broken-reference) specification was designed with security & transparency in mind, so it enforces that all scripts have [**homepage**](../../sbuild/specification/11.homepage.md) & [**source**](../../sbuild/specification/18.sourceurl.md) links.
4. All <mark style="color:red;">**Unofficial**</mark> packages, also have a [<mark style="color:orange;">**`.note`**</mark>](../../sbuild/specification/15.note.md)which clearly state that it's a **Community Created Package** & Where to reach/report if any issues arise.
