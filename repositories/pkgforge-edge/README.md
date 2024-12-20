---
icon: atom
description: The Official Repository containing the latest bleeding edge binaries/packages
---

# pkgforge-edge

{% hint style="warning" %}
By [<mark style="color:purple;">**Repo**</mark>](https://soar.qaidvoid.dev/configuration#repository-configuration), **we mean** [**Soar's repository**](https://soar.qaidvoid.dev/configuration#repository-configuration) **& NOT GitHub Repository**
{% endhint %}

{% hint style="success" %}
* [x] This [repo](https://soar.qaidvoid.dev/configuration#repository-configuration) combines [Broken link](broken-reference "mention") & [Broken link](broken-reference "mention")
* [x] This is the **bleeding-edge** version i.e all packages are latest & contain no snapshots
* [x] For stability, versioning & snapshots, Please refer to [pkgforge-stable](../pkgforge-stable/ "mention")
{% endhint %}

### [Config](https://soar.qaidvoid.dev/configuration#repository-configuration)

<pre class="language-jsonp"><code class="lang-jsonp">{
  "repositories": [
<strong>    {
</strong>      "name": "pkgforge-edge",
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
</code></pre>
