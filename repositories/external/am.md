---
icon: user-bounty-hunter
description: Application Manager (AM)
---

# AM

{% hint style="info" %}
* [x] Project: [https://github.com/ivan-hc/AM](https://github.com/ivan-hc/AM)&#x20;
* [x] Bugs/Issues: [https://github.com/ivan-hc/AM/issues](https://github.com/ivan-hc/AM/issues)
* [x] Soar Repo: <mark style="color:orange;">**`ivan-hc-am`**</mark>
* [x] Cache: [https://huggingface.co/datasets/pkgforge/AMcache](https://huggingface.co/datasets/pkgforge/AMcache)
* [x] Soar CI & Repo: [https://github.com/pkgforge-community/AM-HF-SYNC](https://github.com/pkgforge-community/AM-HF-SYNC)
* [x] Metadata: [https://meta.pkgforge.dev/external/am/](https://meta.pkgforge.dev/external/am/)
* [x] Type: AppImages
{% endhint %}

***

### Add

{% hint style="info" %}
[Using <mark style="color:orange;">**`soar defconfig`**</mark>](#user-content-fn-1)[^1]  (<mark style="color:green;">**Recommended**</mark>)&#x20;

{% code overflow="wrap" %}
```bash
#ONLY If you didn't already use it or have your own custom config
soar defconfig --external
soar sync
soar list 'ivan-hc-am'
```
{% endcode %}
{% endhint %}

{% hint style="info" %}
[Using your text editor](#user-content-fn-2)[^2] \[ <mark style="color:orange;">**`~/.config/soar/config.toml`**</mark> ]

* [x] Open it in a text editor

{% code overflow="wrap" %}
```bash
#Open the config file using your favourtie editor
#In this example, we will use micro
mkdir -pv "~/.config/soar" &&\
 micro "~/.config/soar/config.toml"
```
{% endcode %}

* [x] Add the repo config

{% code overflow="wrap" %}
```toml
[[repositories]]
name = "ivan-hc-am"
url = "https://meta.pkgforge.dev/external/am/x86_64-Linux.json.zstd"
```
{% endcode %}

* [x] Sync metadata

{% code overflow="wrap" %}
```bash
soar sync
soar list 'ivan-hc-am'
```
{% endcode %}
{% endhint %}

{% hint style="info" %}
[Using tee (<mark style="color:red;">**NOT-Recommended**</mark>)](#user-content-fn-3)[^3]

* [x] Append

{% code overflow="wrap" %}
```bash
mkdir -pv "~/.config/soar" &&\
tee -a "~/.config/soar/config.toml" <<EOF
[[repositories]]
name = "ivan-hc-am"
url = "https://meta.pkgforge.dev/external/am/x86_64-Linux.json.zstd"
EOF
```
{% endcode %}

* [x] Sync metadata

```bash
soar sync
soar list 'ivan-hc-am'
```
{% endhint %}

[^1]: Assuming you didn't run this before and you DO NOT have your own custom config at <mark style="color:orange;">**`~/.config/soar/config.toml`**</mark>

[^2]: Should use if using custom config or the above command fails

[^3]: Should only use if you can't use a text editor or want to do it non-interactively
