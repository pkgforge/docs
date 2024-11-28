---
icon: atom
description: The Official Repository containing the latest bleeding edge binaries/packages
---

# pkgforge-edge

{% hint style="info" %}
* [x] This repo combines [toolpacks-bincache](../../orgs/pkgforge-core/projects/toolpacks-bincache/ "mention") & [pkgcache](../../orgs/pkgforge-core/projects/pkgcache/ "mention")
* [x] This is the bleeding-edge version i.e all packages are latest & contain no snapshots
* [x] For stability, versioning & snapshots, Please refer to [pkgforge-stable](../pkgforge-stable/ "mention")
{% endhint %}

```json5
{
  "repositories": [
    {
      "name": "pkgforge-edge",
      "url": "https://bin.pkgforge.dev/x86_64",
      "metadata": "METADATA.AIO.json",
      "sources": {
        "bin": "https://bin.pkgforge.dev/x86_64",
        "base": "https://bin.pkgforge.dev/x86_64/Baseutils",
        "pkg": "https://pkg.pkgforge.dev/x86_64"
      }
    }
  ]
}
```
