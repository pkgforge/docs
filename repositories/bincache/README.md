---
icon: box-circle-check
description: The Official Repository containing the latest bleeding edge binaries/packages
---

# bincache

WIP

{% hint style="warning" %}
By [<mark style="color:purple;">**Repo**</mark>](https://soar.qaidvoid.dev/configuration#repository-configuration), **we mean** [**Soar's repository**](https://soar.qaidvoid.dev/configuration#repository-configuration) **& NOT GitHub Repository**
{% endhint %}

{% hint style="success" %}
* [x] This [repo](https://soar.qaidvoid.dev/configuration#repository-configuration) combines [Broken link](broken-reference "mention") & [Broken link](broken-reference "mention")
* [x] This is the **bleeding-edge** version i.e all packages are latest & contain no snapshots
* [x] For stability, versioning & snapshots, Please refer to [pkgcache](../pkgcache/ "mention")
{% endhint %}

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
