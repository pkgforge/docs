---
icon: download
description: Hosted Binary Cache
---

# Cache

### GitHub Container Registry

{% hint style="success" %}
* The prebuilt binaries are stored on [<mark style="color:orange;">**PkgForge's Github Organization**</mark>](https://github.com/orgs/pkgforge/packages) at: [https://github.com/orgs/pkgforge/packages?repo\_name=bincache](https://github.com/orgs/pkgforge/packages?repo_name=bincache)
* This is achieved with [oras](https://github.com/oras-project/oras) & allows us to use [Github Container Registry](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry) for a transparent & complete history (tags) of all previous versions.
* This is our primary cache, and the rest are backups based on this one.
{% endhint %}

***

### GitHub Releases

{% hint style="warning" %}
* The prebuilt binaries are also mirrored at: [https://github.com/pkgforge/bincache/releases](https://github.com/pkgforge/bincache/releases)
* This is achieved by redownloading ghcr packages and then reuploading them to Github Releases
* This is our secondary cache, and <mark style="color:red;">**may not have all the packages**</mark> due to [**github rate limits**](https://docs.github.com/en/graphql/overview/rate-limits-and-node-limits-for-the-graphql-api#primary-rate-limit) , is usually a week behind the main cache & serves as backup in case [ghcr](https://ghcr.io/) goes down
{% endhint %}

***

### HuggingFace Hub

{% hint style="warning" %}
* The prebuilt binaries are also stored on [<mark style="color:orange;">**Pkgforge's Hugging Face**</mark>](https://huggingface.co/pkgforge) Repository at: [https://huggingface.co/datasets/pkgforge/bincache](https://huggingface.co/datasets/pkgforge/bincache)
* This is achieved with git-lfs & allows us to have a transparent & complete history (snapshots) of all previous versions.
* This is our secondary cache, and <mark style="color:red;">**may not have all the packages**</mark>, is usually a week behind the main cache & serves as backup in case [ghcr](https://ghcr.io/) goes down
{% endhint %}

***

### CloudFlare R2

{% hint style="danger" %}
* Some of the prebuilt binaries are also stored on [<mark style="color:orange;">**Pkgforge's CloudFlare**</mark>](https://developers.cloudflare.com/r2/)[ <mark style="color:orange;">**R2 Bucket**</mark> ](https://developers.cloudflare.com/r2/)at:  [https://bin.pkgforge.dev/](https://bin.pkgforge.dev/)
* This is achieved with  [rClone](https://github.com/rclone/rclone) & allows us to have the most reliable & fastest access to the core binaries we depend on.
* **This cache reserve does NOT contain everything & is meant for pkgforge's CI use only**
{% endhint %}
