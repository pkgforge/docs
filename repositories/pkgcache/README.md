---
icon: box-circle-check
description: The Official Repository containing stable/versioned binaries/packages
---

# pkgcache

## PkgCache

{% embed url="https://bin.pkgforge.dev/list.gif?tmp.h0ks9eLr5x=tmp.W4yp8aEjaT" %}
[**Package Forge Package Cache**](https://github.com/pkgforge/pkgcache)
{% endembed %}

* This repository [**builds, compiles & bundles**](https://github.com/pkgforge/pkgcache/actions) <mark style="color:orange;">**SoarPkgs**</mark> & provides **PreBuilt Package Cache** for [**Soar**](https://github.com/pkgforge/soar)**.**

{% hint style="success" %}
- [x] This [repo](https://soar.qaidvoid.dev/configuration#repository-configuration)&#x20;
- [x] This is the **stable** version, i.e. all packages are stable with **versions** & **snapshots**
- [x] Workflow: [https://github.com/Azathothas/Toolpacks-BinCache-Importer/actions/workflows/import\_sync.yaml](https://github.com/Azathothas/Toolpacks-BinCache-Importer/actions/workflows/import_sync.yaml)
- [x] Scripts: [https://github.com/Azathothas/Toolpacks-BinCache-Importer/tree/main/.github/scripts](https://github.com/Azathothas/Toolpacks-BinCache-Importer/tree/main/.github/scripts)
- [x] For the **bleeding-edge** latest & greatest, Please refer to [bincache](../bincache/ "mention")
{% endhint %}

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
