---
icon: webhook
description: The Official Soar User Repository (SoarPkgs)
---

# pkgforge-community

{% hint style="warning" %}
By [<mark style="color:purple;">**Repo**</mark>](https://soar.qaidvoid.dev/configuration#repository-configuration), **we mean** [**Soar's repository**](https://soar.qaidvoid.dev/configuration#repository-configuration) **& NOT GitHub Repository**
{% endhint %}

{% hint style="success" %}
* [x] &#x20;[**Soarpkgs**](../../orgs/pkgforge-core/projects/soarpkgs/) is the **Official Soar User Repository**, kind of like the [AUR](https://wiki.archlinux.org/title/Arch_User_Repository), as such all recipes <mark style="color:purple;">(</mark>[<mark style="color:purple;">**`SBUILD`**</mark>](broken-reference)) are built & installed locally. You can read more at: [https://docs.pkgforge.dev/orgs/pkgforge-core/projects/soarpkgs/differences](https://docs.pkgforge.dev/orgs/pkgforge-core/projects/soarpkgs/differences)
* [x] This [repo](https://soar.qaidvoid.dev/configuration#repository-configuration) is **just an alias** to [**Soarpkgs**](../../orgs/pkgforge-core/projects/soarpkgs/)
* [x] This [repo](https://soar.qaidvoid.dev/configuration#repository-configuration) is **NOT TO BE CONFUSED** with [https://github.com/pkgforge-community](https://github.com/pkgforge-community) (This is an ORG,  [**Soarpkgs**](../../orgs/pkgforge-core/projects/soarpkgs/) uses it to store forked repos)
* [x] If you want to install prebuilt [Binaries](../../formats/binaries/) & [Packages](../../formats/packages/), Please use [**pkgforge-edge**](https://docs.pkgforge.dev/repositories/pkgforge-edge) **or** [**pkgforge-stable**](https://docs.pkgforge.dev/repositories/pkgforge-stable)
{% endhint %}

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
