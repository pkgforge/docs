---
description: >-
  Usually extract & run (or even Self Extractable) archives provided by official
  sources themselves.
icon: box-taped
---

# Archive

{% hint style="success" %}
<mark style="color:orange;">**Build Profile**</mark>

* [x] Repackage with [wrappe](https://github.com/Systemcluster/wrappe) if upstream source is already portable
* [x] Repackage with [sharun](https://github.com/VHSgunzo/sharun) + [wrappe](https://github.com/Systemcluster/wrappe)/[uruntime](https://github.com/VHSgunzo/uruntime) if upstream source is not portable
{% endhint %}

{% hint style="success" %}
<mark style="color:purple;">**Sources**</mark>

* Upstream source if they release a portable archive
* Distro Package or Registries like npm, pypi etc if prebuilt upstream doesn't exist
{% endhint %}

{% hint style="warning" %}
**`Nomenclature`**

* **`*sharun*`** : Implies it was packaged with [**sharun**](https://github.com/VHSgunzo/sharun)
* **`*wrappe*`** : Implies it was packaged with [**wrappe**](https://github.com/Systemcluster/wrappe)
* **`*source*`** : Implies it was build from source & then packaged
* **`*stable*`** : Implies a prebuilt was fetched & then packages
* **`*npm*`** : Implies it was packaged from a [**npm**](https://www.npmjs.com/) package
* **`*pypi*`** : Implies it was packaged from a [**pypi**](https://pypi.org/) package
{% endhint %}
