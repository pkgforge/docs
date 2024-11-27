---
icon: server
description: Build & CI Servers
---

# Infra

### Cost

* Servers & Storage cost money, right now all financial cost is covered solely by [**@Azathothas**](https://docs.pkgforge.dev/orgs/pkgforge-core/people#azathothas)&#x20;
* [HuggingFace](https://huggingface.co/pricing) (<mark style="color:orange;">`$9/Month`</mark>)&#x20;
* [CloudFlare R2 Bucket](https://developers.cloudflare.com/r2/pricing/) (<mark style="color:orange;">`70-100$/Month`</mark>)&#x20;
* [Self Hosted Github Runners](https://docs.github.com/en/actions/hosting-your-own-runners/managing-self-hosted-runners/about-self-hosted-runners) (<mark style="color:orange;">`36$/Month`</mark>)

<table><thead><tr><th width="129">Builder</th><th width="181">Specs</th><th width="104">Host</th><th>Dedicated ?</th><th width="116">Build Time</th><th>Cost</th></tr></thead><tbody><tr><td><a href="https://github.com/Azathothas/Toolpacks/actions/workflows/build_aarch64_Linux.yaml"><code>aarch64</code> <code>Linux</code></a></td><td><code>14 vCPU (Ampere Altra)</code> <code>+</code> <code>32 GB RAM (??)</code> <code>+</code> <code>1024 GB SSD</code> <code>+</code> <code>Unmetered Bandwidth</code></td><td><a href="https://www.netcup.eu/bestellen/produkt.php?produkt=3991">Netcup</a></td><td><code>NO</code></td><td><code>35-40</code> <code>Hrs</code></td><td><code>$17/Mo</code></td></tr><tr><td><a href="https://github.com/Azathothas/Toolpacks/actions/workflows/build_x86_64_Linux.yaml"><code>x86_64</code> <code>Linux</code></a></td><td><code>8 vCPU (AMD EPYC™ 9634)</code> <code>+</code> <code>16 GB RAM (DDR5 ECC)</code> <code>+</code> <code>512 GB SSD</code> <code>+</code> <code>Unmetered Bandwidth</code></td><td><a href="https://www.netcup.eu/bestellen/produkt.php?produkt=3694">Netcup</a></td><td><a href="https://www.netcup.eu/vserver/vergleich-root-server-vps.php"><code>Semi-Dedicated</code></a></td><td><code>20-25</code> <code>Hrs</code></td><td><code>$18.50/Mo</code></td></tr></tbody></table>

* Test Servers  (<mark style="color:orange;">`12$/Month`</mark>)

<table><thead><tr><th width="129">Builder</th><th width="181">Specs</th><th width="104">Host</th><th>Dedicated ?</th><th>Cost</th></tr></thead><tbody><tr><td><code>aarch64</code> <code>Linux</code></td><td><code>6 vCPU (Ampere Altra)</code> <code>+</code> <code>8 GB RAM +</code> <code>256 GB SSD</code> <code>+</code> <code>Unmetered Bandwidth</code></td><td><a href="https://www.netcup.com/en/server/arm-server/vps-1000-arm-g11-iv-mnz">Netcup</a></td><td><code>NO</code></td><td><code>$6/Mo</code></td></tr><tr><td><code>x86_64</code> <code>Linux</code></td><td><code>4 vCPU +</code> 8<code>GB RAM + 256 GB SSD</code> <code>+</code> <code>Unmetered Bandwidth</code></td><td><a href="https://www.netcup.com/en/server/vps/vps-1000-g11-12m-iv">Netcup</a></td><td><code>No</code></td><td><code>$6/Mo</code></td></tr></tbody></table>

{% hint style="warning" %}
[bin.pkgforge.dev](https://bin.pkgforge.dev) is not a real webserver. It is a [r2 bucket](https://developers.cloudflare.com/r2/), and loads all objects upon each request. Thus, the load times are very slow & you are better of using [**Soar**](https://github.com/pkgforge/soar)
{% endhint %}
