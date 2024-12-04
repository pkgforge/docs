---
icon: atom-simple
description: The Official Repository containing stable/versioned binaries/packages
---

# pkgforge-stable

{% hint style="warning" %}
By [<mark style="color:purple;">**Repo**</mark>](https://soar.qaidvoid.dev/configuration#repository-configuration), **we mean** [**Soar's repository**](https://soar.qaidvoid.dev/configuration#repository-configuration) **& NOT GitHub Repository**
{% endhint %}

{% hint style="success" %}
* [x] This [repo](https://soar.qaidvoid.dev/configuration#repository-configuration) combines [Broken link](broken-reference "mention") & [Broken link](broken-reference "mention")
* [x] This is the **stable** version, i.e. all packages are stable with **versions** & **snapshots**
* [x] Workflow: [https://github.com/Azathothas/Toolpacks-BinCache-Importer/actions/workflows/import\_sync.yaml](https://github.com/Azathothas/Toolpacks-BinCache-Importer/actions/workflows/import_sync.yaml)
* [x] Scripts: [https://github.com/Azathothas/Toolpacks-BinCache-Importer/tree/main/.github/scripts](https://github.com/Azathothas/Toolpacks-BinCache-Importer/tree/main/.github/scripts)
* [x] For the **bleeding-edge** latest & greatest, Please refer to [pkgforge-edge](../pkgforge-edge/ "mention")
{% endhint %}

### [Config](https://soar.qaidvoid.dev/configuration#repository-configuration)

{% code overflow="wrap" %}
```jsonp
{
  "repositories": [
    {
      "name": "pkgforge-stable",
      "url": "https://bincache.pkgforge.dev/x86_64",
      "metadata": "METADATA.AIO.json",
      "sources": {
        "bin": "https://bincache.pkgforge.dev/x86_64",
        "base": "https://bincache.pkgforge.dev/x86_64/Baseutils",
        "pkg": "https://pkgcache.pkgforge.dev/x86_64"
      }
    }
  ]
}
```
{% endcode %}
