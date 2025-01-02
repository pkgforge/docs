---
icon: box-circle-check
description: 📀 Pre-Built Portable Packages for Soar (SoarPkgs)
---

# pkgcache

{% embed url="https://bin.pkgforge.dev/list.gif?tmp.049f802DRI=tmp.Q2E6euzrSo" %}
📀 **Pre-Built** [**Portable Packages**](../../formats/packages/) for [**Soar**](https://github.com/pkgforge/soar) ([**SoarPkgs**](https://github.com/pkgforge/soarpkgs))
{% endembed %}

* [**PkgCache**](https://github.com/pkgforge/pkgcache) provides📀 [**Pre-Built**](cache.md) [**Portable Packages**](../../formats/packages/) for [**Soar**](https://github.com/pkgforge/soar) ([**SoarPkgs**](https://github.com/pkgforge/soarpkgs))
* [Build recipes](https://github.com/pkgforge/bincache/blob/main/SBUILD_LIST.json) (<mark style="color:purple;">**`SBUILD`**</mark>) are built from source & uploaded to the [**Cache**](cache.md).
* Only formats listed at [https://docs.pkgforge.dev/formats/packages](https://docs.pkgforge.dev/formats/packages) are applicable.
* Only recipes that meet the criteria listed at [https://docs.pkgforge.dev/repositories/pkgcache/package-request#criteria](https://docs.pkgforge.dev/repositories/pkgcache/package-request#criteria) are applicable
* For a more detailed comparison/differences, refer to: [differences.md](../soarpkgs/differences.md "mention")

### [Config](https://soar.qaidvoid.dev/configuration#repository-configuration)

{% code overflow="wrap" %}
```jsonp
{
  "repositories": [
    {
      "name": "pkgcache",
      "url": "https://pkgcache.pkgforge.dev/x86_64",
      "metadata": "METADATA.json",
      "sources": {
        "ghcr": "https://pkgcache.pkgforge.dev/x86_64",
        "hf": "https://pkgcache-hf.pkgforge.dev/x86_64",
        "r2": "https://pkgcache-r2.pkgforge.dev/x86_64"
      }
    }
  ]
}
```
{% endcode %}
