---
icon: atom-simple
description: The Official Repository containing stable/versioned binaries/packages
---

# pkgforge-stable

{% hint style="success" %}
* This repo combines [toolpacks-bincache](../../orgs/pkgforge-core/projects/toolpacks-bincache/ "mention") & [pkgcache](../../orgs/pkgforge-core/projects/pkgcache/ "mention")
* This is the **stable** version, i.e. all packages are stable with **versions** & **snapshots**
* Workflow: [https://github.com/Azathothas/Toolpacks-BinCache-Importer/actions/workflows/import\_sync.yaml](https://github.com/Azathothas/Toolpacks-BinCache-Importer/actions/workflows/import_sync.yaml)
* Scripts: [https://github.com/Azathothas/Toolpacks-BinCache-Importer/tree/main/.github/scripts](https://github.com/Azathothas/Toolpacks-BinCache-Importer/tree/main/.github/scripts)
* For the **bleeding-edge** latest & greatest, Please refer to [pkgforge-edge](../pkgforge-edge/ "mention")
{% endhint %}

### Config

{% code overflow="wrap" %}
```json
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

