---
description: Officially maintained External Repo for All Crates
icon: rust
---

# pkgforge-cargo

{% hint style="info" %}
* [x] Project: [https://github.com/pkgforge-cargo/builder](https://github.com/pkgforge-cargo/builder)
* [x] Bugs/Issues: [https://github.com/pkgforge-cargo/builder/issues](https://github.com/pkgforge-cargo/builder/issues)
* [x] Soar Repo: <mark style="color:orange;">**`pkgforge-cargo`**</mark>
* [x] Cache: [<mark style="color:green;">**Yes**</mark>](#user-content-fn-1)[^1]
* [x] Soar CI & Repo: [https://github.com/pkgforge-cargo/builder/tree/main/scripts](https://github.com/pkgforge-cargo/builder/tree/main/scripts)
* [x] Metadata: [https://github.com/pkgforge-cargo/builder/tree/main/data](https://github.com/pkgforge-cargo/builder/tree/main/data)
* [x] Type: Static
{% endhint %}

***

### Trust

{% hint style="success" %}
This is as good as our own officially curated packages, as it is officially maintained by [@Azathothas](https://docs.pkgforge.dev/orgs/readme/people#azathothas). We have [clear workflow](https://github.com/pkgforge-cargo/builder/tree/main#-workflow) on what & how packages are built. And since the packages are built on [Github Actions](https://github.com/pkgforge-cargo/builder/actions/workflows/matrix_builds.yaml), transparent CI logs are also available for all of the packages.

All of these make us say with high confidence that **you can trust it, as long as you trust that Github, Cargo, Crates.io or the package itself isn't compromised.**

On a scale of <mark style="color:orange;">**1-10**</mark>, we had rate this source as <mark style="color:green;">**9**</mark>, **As this is an officially maintained external source**.
{% endhint %}

***

### Add

{% hint style="success" %}
A fresh/new install of soar will have this repository enabled by default.
{% endhint %}

{% hint style="info" %}
[Using <mark style="color:orange;">**`soar defconfig`**</mark>](#user-content-fn-2)[^2]  (<mark style="color:green;">**Recommended**</mark>)&#x20;

{% code overflow="wrap" %}
```bash
#ONLY If you didn't already use it or have your own custom config
soar defconfig
soar sync
soar list 'pkgforge-cargo'
```
{% endcode %}
{% endhint %}

{% hint style="info" %}
[Using your text editor](#user-content-fn-3)[^3] \[ <mark style="color:orange;">**`~/.config/soar/config.toml`**</mark> ]

* [x] Open it in a text editor

{% code overflow="wrap" %}
```bash
#Open the config file using your favourtie editor
#In this example, we will use micro
mkdir -pv "~/.config/soar" &&\
 micro "~/.config/soar/config.toml"
```
{% endcode %}

* [x] Add the repo config (For other hosts, see [supported list](https://github.com/pkgforge-cargo/builder#-hosts---targets).)

{% code overflow="wrap" %}
```toml
[[repositories]]
name = "pkgforge-cargo"
url = "https://meta.pkgforge.dev/external/pkgforge-cargo/x86_64-Linux.sdb.zstd"
```
{% endcode %}

* [x] Sync metadata

{% code overflow="wrap" %}
```bash
soar sync
soar list 'pkgforge-cargo'
```
{% endcode %}
{% endhint %}

{% hint style="info" %}
[Using tee (<mark style="color:red;">**NOT-Recommended**</mark>)](#user-content-fn-4)[^4]

* [x] Append (For other hosts, see [supported list](https://github.com/pkgforge-cargo/builder#-hosts---targets).)

{% code overflow="wrap" %}
```bash
mkdir -pv "~/.config/soar" &&\
tee -a "~/.config/soar/config.toml" <<EOF
[[repositories]]
name = "pkgforge-cargo"
url = "https://meta.pkgforge.dev/external/pkgforge-cargo/x86_64-Linux.sdb.zstd"
EOF
```
{% endcode %}

* [x] Sync metadata

```bash
soar sync
soar list 'pkgforge-cargo'
```
{% endhint %}

[^1]: Packages are stored on ghcr

[^2]: Assuming you didn't run this before and you DO NOT have your own custom config at <mark style="color:orange;">**`~/.config/soar/config.toml`**</mark>

[^3]: Should use if using custom config or the above command fails

[^4]: Should only use if you can't use a text editor or want to do it non-interactively
