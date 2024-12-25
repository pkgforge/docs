---
description: Hosted Binary Cache
icon: download
---

# Cache

* The prebuilt binaries are stored on [<mark style="color:orange;">**Pkgforge's CloudFlare**</mark>](https://developers.cloudflare.com/r2/)[ <mark style="color:orange;">**R2 Bucket**</mark> ](https://developers.cloudflare.com/r2/)at:  [**https://bin.pkgforge.dev/**](https://bin.pkgforge.dev/)
* This is achieved with  [rClone](https://github.com/rclone/rclone) & a snapshot version of the entire bucket is [**also Synced**](https://github.com/Azathothas/Toolpacks-BinCache-Importer) to [<mark style="color:orange;">**Pkgforge's Hugging Face**</mark>](https://huggingface.co/pkgforge) Repository at: [https://huggingface.co/datasets/pkgforge/bincache](https://huggingface.co/datasets/pkgforge/bincache)

{% hint style="info" %}
The Repository at: [https://huggingface.co/datasets/pkgforge/bincache](https://huggingface.co/datasets/pkgforge/bincache) might show some files as <mark style="color:red;">**unsafe**</mark>, this is because [Binaries](../../../../formats/binaries/) are also packed using [<mark style="color:orange;">**`upx --best`**</mark>](https://github.com/upx/upx/blob/devel/doc/upx-doc.txt#L114) after a [CI Build is Complete.](https://github.com/Azathothas/Toolpacks/actions)&#x20;

* It is a known issue: [https://github.com/upx/upx/issues/437](https://github.com/upx/upx/issues/437)
{% endhint %}

* Currently, the [**CI rebuilds**](https://github.com/Azathothas/Toolpacks/actions) everything <mark style="color:purple;">**`@30 18 * * 1`**</mark>
