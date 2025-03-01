---
description: cargo-binstall/cargo-quickinstall
icon: crab
---

# cargo-bins

{% hint style="info" %}
* [x] Project: [https://github.com/cargo-bins/cargo-quickinstall](https://github.com/cargo-bins/cargo-quickinstall)
* [x] Bugs/Issues: [https://github.com/cargo-bins/cargo-quickinstall/issues](https://github.com/cargo-bins/cargo-quickinstall/issues)
* [x] Soar Repo: <mark style="color:orange;">**`cargo-bins`**</mark>
* [x] Cache: [<mark style="color:red;">**None**</mark>](#user-content-fn-1)[^1]
* [x] Soar CI & Repo: [https://github.com/pkgforge/metadata/tree/main/external/cargo-bins/scripts](https://github.com/pkgforge/metadata/tree/main/external/cargo-bins/scripts)
* [x] Metadata: [https://github.com/pkgforge/metadata/tree/main/external/cargo-bins/data](https://github.com/pkgforge/metadata/tree/main/external/cargo-bins/data)
* [x] Type: Static/Dynamic Binaries (Latest Only)
{% endhint %}

***

### Add

{% hint style="info" %}
[Using <mark style="color:orange;">**`soar defconfig`**</mark>](#user-content-fn-2)[^2]  (<mark style="color:green;">**Recommended**</mark>)&#x20;

{% code overflow="wrap" %}
```bash
#ONLY If you didn't already use it or have your own custom config
soar defconfig --external
soar sync
soar list 'cargo-bins'
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

* [x] Add the repo config

{% code overflow="wrap" %}
```toml
[[repositories]]
name = "cargo-bins"
url = "https://meta.pkgforge.dev/external/cargo-bins/x86_64-Linux.json.zstd"
```
{% endcode %}

* [x] Sync metadata

{% code overflow="wrap" %}
```bash
soar sync
soar list 'cargo-bins'
```
{% endcode %}
{% endhint %}

{% hint style="info" %}
[Using tee (<mark style="color:red;">**NOT-Recommended**</mark>)](#user-content-fn-4)[^4]

* [x] Append

{% code overflow="wrap" %}
```bash
mkdir -pv "~/.config/soar" &&\
tee -a "~/.config/soar/config.toml" <<EOF
[[repositories]]
name = "cargo-bins"
url = "https://meta.pkgforge.dev/external/cargo-bins/x86_64-Linux.json.zstd"
EOF
```
{% endcode %}

* [x] Sync metadata

```bash
soar sync
soar list 'cargo-bins'
```
{% endhint %}

[^1]: This project already releases prebuilt as github release

[^2]: Assuming you didn't run this before and you DO NOT have your own custom config at <mark style="color:orange;">**`~/.config/soar/config.toml`**</mark>

[^3]: Should use if using custom config or the above command fails

[^4]: Should only use if you can't use a text editor or want to do it non-interactively
