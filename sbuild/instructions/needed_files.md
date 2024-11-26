---
description: Files produced at end of a successful SBUILD
icon: list-check
---

# NEEDED\_FILES

* [x] <mark style="color:orange;">**`${SBUILD_OUTDIR}/${SBUILD_PKG}`**</mark>

{% hint style="info" %}
- [x] **Description**: The actual <mark style="color:orange;">**binary/package**</mark> that was built
- [x] **Min\_Size**: <mark style="color:orange;">**`> 100KB`**</mark>
{% endhint %}

* [x] <mark style="color:orange;">**`${SBUILD_OUTDIR}/.desktop`**</mark> | <mark style="color:orange;">**`${SBUILD_OUTDIR}/${SBUILD_PKG}.desktop`**</mark>

{% hint style="info" %}
- [x] **Description**: <mark style="color:purple;">**`Desktop`**</mark>**&#x20;**<mark style="color:orange;">**File**</mark>, Is _Edited/Fixed during Integration_
- [x] **Min\_Size**: <mark style="color:orange;">**`> 3BYTES`**</mark>
- [x] Only Available for [**Packages**](../../formats/packages/) **NOT** for [**Binaries**](../../formats/binaries/)
{% endhint %}

* [x] <mark style="color:orange;">**`${SBUILD_OUTDIR}/.DirIcon`**</mark> | <mark style="color:orange;">**`${SBUILD_OUTDIR}/${SBUILD_PKG}.DirIcon`**</mark>

{% hint style="info" %}
- [x] **Description**: <mark style="color:orange;">**`DirIcon`**</mark>, _Preferred as_ <mark style="color:purple;">**`Icon`**</mark> **if** <mark style="color:orange;">**${SBUILD\_OUTDIR}/${SBUILD\_PKG}.png**</mark> OR <mark style="color:orange;">**${SBUILD\_OUTDIR}/${SBUILD\_PKG}.svg**</mark> **DO NOT Exist**
- [x] **Min\_Size**: <mark style="color:orange;">**`> 1KB`**</mark>
- [x] Only Available for [**Packages**](../../formats/packages/) **NOT** for [**Binaries**](../../formats/binaries/)
{% endhint %}

* [x] <mark style="color:orange;">**`${SBUILD_OUTDIR}/${SBUILD_PKG}.png`**</mark> | <mark style="color:orange;">**`${SBUILD_OUTDIR}/${SBUILD_PKG}.svg`**</mark>

{% hint style="info" %}
- [x] **Description**: _Preferred even_ **if&#x20;**<mark style="color:orange;">**${SBUILD\_OUTDIR}/${SBUILD\_PKG}.png**</mark> OR <mark style="color:orange;">**${SBUILD\_OUTDIR}/${SBUILD\_PKG}.svg**</mark> **Exists due to Higher Resolution**
- [x] **Min\_Size**: <mark style="color:orange;">**`> 1KB`**</mark>
- [x] Only Available for [**Packages**](../../formats/packages/) **NOT** for [**Binaries**](../../formats/binaries/)
{% endhint %}

* [x] <mark style="color:orange;">**`${SBUILD_OUTDIR}/${SBUILD_PKG}.appdata.xml`**</mark> | <mark style="color:orange;">**`${SBUILD_OUTDIR}/${SBUILD_PKG}.metainfo.xml`**</mark>

{% hint style="info" %}
- [x] **Description**: _Prefer_ <mark style="color:orange;">**metainfo.xml**</mark> over <mark style="color:orange;">**appdata.xml**</mark> as _<mark style="color:orange;">appdata.xml</mark> is now Legacy_
- [x] **Min\_Size**: <mark style="color:orange;">**`> 3BYTES`**</mark>
- [x] Only Available for [**Packages**](../../formats/packages/) **NOT** for [**Binaries**](../../formats/binaries/)
{% endhint %}

* [x] <mark style="color:orange;">**`${SBUILD_OUTDIR}/.version`**</mark> | <mark style="color:orange;">**`${SBUILD_OUTDIR}/${SBUILD_PKG}.version`**</mark>

{% hint style="info" %}
**Description**: <mark style="color:purple;">**`Version`**</mark> <mark style="color:orange;">**File**</mark>, Contains Version, _if empty, then Use Version based on_ <mark style="color:orange;">**Date**</mark>/<mark style="color:orange;">**BSUM**</mark>
{% endhint %}