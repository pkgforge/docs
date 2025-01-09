---
icon: box-open-full
description: The Official Soar User Repository (SoarPkgs)
---

# soarpkgs

## SoarPkgs

{% embed url="https://bin.pkgforge.dev/list.gif?tmp.8lEm33PR7H=tmp.fPi85ABfDA" %}
[**The true, simple & suckless Linux User Repository**](https://github.com/pkgforge/soarpkgs)
{% endembed %}

* &#x20;[**Soarpkgs**](https://github.com/pkgforge/soarpkgs) is the **Official Soar User Repository**, kind of like the [AUR](https://wiki.archlinux.org/title/Arch_User_Repository), and contains all the Build recipes ([<mark style="color:purple;">**`SBUILD`**</mark>](broken-reference))
* Build recipes ([<mark style="color:purple;">**`SBUILD`**</mark>](broken-reference)) are built & installed from source. This repo in of itself contains no prebuilt artifacts.&#x20;
* Packages are first added here before being added to [**`bincache`**](../bincache/)/[**`pkgcache`**](../pkgcache/) based on **certain criteria** with some **major differences**.
* If you want to install prebuilt [Binaries](../../formats/binaries/) & [Packages](../../formats/packages/), Please refer to [bincache](../bincache/ "mention") & [pkgcache](../pkgcache/ "mention")respectively
* For a more detailed comparison/differences, refer to: [differences.md](differences.md "mention")

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
