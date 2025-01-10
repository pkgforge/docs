---
icon: server
description: Build & CI Servers
---

# Infra

### Workflow

* Either [Github-Runners](https://docs.github.com/en/actions/using-github-hosted-runners/about-github-hosted-runners/about-github-hosted-runners) OR [Self-Hosted Runners](infra.md#cost) are configured and kicked once a week.
* The stack runs on a combination of [Podman](https://podman.io/) + [Docker](https://www.docker.com/)
* Primary artifacts are stored on [ghcr](https://docs.pkgforge.dev/repositories/bincache/cache#github-container-registry), with mirrors on both [Cloudflare R2](https://docs.pkgforge.dev/repositories/bincache/cache#cloudflare-r2) & [HuggingFace](https://docs.pkgforge.dev/repositories/bincache/cache#huggingface-hub)

### Cost

{% hint style="info" %}
Same Infra is shared with [pkgcache](../pkgcache/ "mention")
{% endhint %}

* Servers & Storage cost money, right now all financial cost is covered solely by [**@Azathothas**](https://docs.pkgforge.dev/orgs/pkgforge-core/people#azathothas)&#x20;
* [HuggingFace](https://huggingface.co/pricing) (<mark style="color:orange;">`$9/Month`</mark>)&#x20;
* [CloudFlare R2 Bucket](https://developers.cloudflare.com/r2/pricing/) + [CloudFlare Workers](https://developers.cloudflare.com/workers/platform/pricing/) & [More](https://www.cloudflare.com/plans/) (<mark style="color:orange;">`70-100$/Month`</mark>)&#x20;
* [Self Hosted Github Runners](https://docs.github.com/en/actions/hosting-your-own-runners/managing-self-hosted-runners/about-self-hosted-runners) (<mark style="color:orange;">`36$/Month`</mark>)

<table><thead><tr><th width="129">Builder</th><th width="181">Specs</th><th width="104">Host</th><th>Dedicated ?</th><th width="116">Build Time</th><th>Cost</th></tr></thead><tbody><tr><td><code>aarch64 Linux</code></td><td>14 vCPU (Ampere Altra) + 32 GB RAM (??) + 1024 GB SSD + Unmetered Bandwidth</td><td><a href="https://www.netcup.eu/bestellen/produkt.php?produkt=3991">Netcup</a></td><td><mark style="color:red;">NO</mark></td><td><code>35-40</code> <code>Hrs</code></td><td><mark style="color:orange;"><code>$17/Mo</code></mark></td></tr><tr><td><code>x86_64 Linux</code></td><td>8 vCPU (AMD EPYC™ 9634) + 16 GB RAM (DDR5 ECC) + 512 GB SSD + Unmetered Bandwidth</td><td><a href="https://www.netcup.eu/bestellen/produkt.php?produkt=3694">Netcup</a></td><td><a href="https://www.netcup.eu/vserver/vergleich-root-server-vps.php"><mark style="color:orange;">Semi-Dedicated</mark></a></td><td><code>20-25</code> <code>Hrs</code></td><td><mark style="color:orange;"><code>$18.50/Mo</code></mark></td></tr></tbody></table>

* Test Servers  (<mark style="color:orange;">`12$/Month`</mark>)

<table><thead><tr><th width="129">Builder</th><th width="181">Specs</th><th width="104">Host</th><th>Dedicated ?</th><th>Cost</th></tr></thead><tbody><tr><td>aarch64 Linux</td><td>6 vCPU (Ampere Altra) + 8 GB RAM + 256 GB SSD + Unmetered Bandwidth</td><td><a href="https://www.netcup.com/en/server/arm-server/vps-1000-arm-g11-iv-mnz">Netcup</a></td><td><mark style="color:red;">NO</mark></td><td><mark style="color:orange;"><code>$6/Mo</code></mark></td></tr><tr><td>x86_64 Linux</td><td>4 vCPU + 8GB RAM + 256 GB SSD + Unmetered Bandwidth</td><td><a href="https://www.netcup.com/en/server/vps/vps-1000-g11-12m-iv">Netcup</a></td><td><mark style="color:red;">NO</mark></td><td><mark style="color:orange;"><code>$6/Mo</code></mark></td></tr></tbody></table>
