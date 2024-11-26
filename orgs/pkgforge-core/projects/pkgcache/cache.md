---
description: Hosted Package Cache
icon: download
---

# Cache

* The prebuilt packages are stored on [<mark style="color:orange;">**Pkgforge's Hugging Face**</mark>](https://huggingface.co/pkgforge) Repository at:  [**https://huggingface.co/datasets/pkgforge/pkgcache/tree/main**](https://huggingface.co/datasets/pkgforge/pkgcache/tree/main)
* This is achieved with git-lfs & allows us to have a transparent & complete history (snapshots) of all previous versions.
* Currently, the [**CI rebuilds**](https://github.com/pkgforge/pkgcache/actions) everything <mark style="color:purple;">**`@0 6 * * 4`**</mark>&#x20;
