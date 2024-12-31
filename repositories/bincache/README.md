---
icon: box-circle-check
description: 📦 Pre-Built Static Binaries for Soar (SoarPkgs)
---

# bincache

{% embed url="https://bin.pkgforge.dev/list.gif?tmp.h3qh1tPN2v=tmp.wp5maNPhvz" %}
📦 **Pre-Built** [**Static Binaries**](../../formats/binaries/) for [**Soar**](https://github.com/pkgforge/soar) ([**SoarPkgs**](https://github.com/pkgforge/soarpkgs))
{% endembed %}

* [**BinCache**](https://github.com/pkgforge/bincache) provides 📦 **Pre-Built** [**Static Binaries**](../../formats/binaries/) for [**Soar**](https://github.com/pkgforge/soar) ([**SoarPkgs**](https://github.com/pkgforge/soarpkgs))
* [Build recipes](https://github.com/pkgforge/bincache/blob/main/SBUILD_LIST.json) (<mark style="color:purple;">**`SBUILD`**</mark>) are built from source & uploaded to the [**Cache**](cache.md).
* Only formats listed at [https://docs.pkgforge.dev/formats/binaries](https://docs.pkgforge.dev/formats/binaries) are applicable.
* Only recipes that meet the criteria listed at [https://docs.pkgforge.dev/repositories/bincache/package-request#criteria](https://docs.pkgforge.dev/repositories/bincache/package-request#criteria) are applicable
* For a more detailed comparison/differences, refer to: [differences.md](differences.md "mention")

### [Config](https://soar.qaidvoid.dev/configuration#repository-configuration)

<pre class="language-jsonp"><code class="lang-jsonp">{
  "repositories": [
<strong>    {
</strong>      "name": "bincache",
      "url": "https://bincache.pkgforge.dev/x86_64",
      "metadata": "METADATA.json",
      "sources": {
        "ghcr": "https://bincache.pkgforge.dev/x86_64",
        "hf": "https://bincache-hf.pkgforge.dev/x86_64",
        "r2": "https://bincache-r2.pkgforge.dev/x86_64"
      }
    }
  ]
}
</code></pre>
