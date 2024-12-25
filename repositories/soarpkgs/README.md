---
icon: webhook
description: The Official Soar User Repository (SoarPkgs)
---

# soarpkgs

## SoarPkgs

{% embed url="https://bin.pkgforge.dev/list.gif?tmp.h0ks9eLr5x=tmp.W4yp8aEjaT" %}
[**Package Forge Community Repo**](https://github.com/pkgforge/soarpkgs)
{% endembed %}

* &#x20;[**Soarpkgs**](broken-reference) is the **Official Soar User Repository**, kind of like the [AUR](https://wiki.archlinux.org/title/Arch_User_Repository), as such all recipes <mark style="color:purple;">(</mark>[<mark style="color:purple;">**`SBUILD`**</mark>](broken-reference)) are built & installed locally. You can read more at: [https://docs.pkgforge.dev/orgs/pkgforge-core/projects/soarpkgs/differences](https://docs.pkgforge.dev/orgs/pkgforge-core/projects/soarpkgs/differences)
* This [repo](https://soar.qaidvoid.dev/configuration#repository-configuration) is **NOT TO BE CONFUSED** with [https://github.com/pkgforge-community](https://github.com/pkgforge-community) (This is an ORG,  [**Soarpkgs**](broken-reference) uses it to store forked repos)
* Packages are first added here before being added to [**`bincache`**](https://github.com/Azathothas/Toolpacks)/[**`pkgcache`**](https://github.com/pkgforge/pkgcache) based on [**certain criteria**](https://docs.pkgforge.dev/orgs/pkgforge-core/projects/pkgcache/package-request#criteria) with some **major differences**.
* If you want to install prebuilt [Binaries](../../formats/binaries/) & [Packages](../../formats/packages/), Please use [**pkgforge-edge**](https://docs.pkgforge.dev/repositories/pkgforge-edge) **or** [**pkgforge-stable**](https://docs.pkgforge.dev/repositories/pkgforge-stable)

### [Config](https://soar.qaidvoid.dev/configuration#repository-configuration)

```json5
{
  "repositories": [
    {
      "name": "pkgforge-community",
      "url": "https://soarpkgs.pkgforge.dev/metadata",
      "metadata": "METADATA.json",
      "sources": {
      }
    }
  ]
}
```
