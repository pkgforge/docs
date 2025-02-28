---
icon: box
description: Statically Linked Binaries (.pkg_type == static)
---

# Static

{% hint style="success" %}
<mark style="color:orange;">**Build Profile**</mark>

* [x] Prefer [**`mimalloc`**](https://github.com/microsoft/mimalloc) over other musl allocators
* [x] Prefer [LTO](https://gcc.gnu.org/wiki/LinkTimeOptimization)
* [x] Prefer [PIE](https://en.wikipedia.org/wiki/Position-independent_code)
{% endhint %}

{% hint style="success" %}
<mark style="color:purple;">**Sources**</mark>

* Most (around 90%) of our **`static`** packages are built from source using standard build tools.
* The rest are fetched from upstream like GitHub Releases etc.
{% endhint %}

{% hint style="warning" %}
<mark style="color:orange;">**`Nomenclature`**</mark>

* **`*source*`** : Implies it was built from source
* **`*official*`** : Implies it was built/fetched from official source
* **`*stable*`** : Implies it was likely fetched from upstream source & not built from source
{% endhint %}
