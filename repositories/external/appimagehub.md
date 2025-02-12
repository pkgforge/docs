---
icon: store
description: AppImage Hub
---

# AppImageHub

{% hint style="info" %}
* [x] Project: [https://www.appimagehub.com/](https://www.appimagehub.com/)
* [x] Bugs/Issues: [https://forum.opendesktop.org/](https://forum.opendesktop.org/)
* [x] Soar Repo: <mark style="color:orange;">**`appimagehub`**</mark>
* [x] Cache: [<mark style="color:red;">**None**</mark>](#user-content-fn-1)[^1]
* [x] Soar CI & Repo: [https://github.com/pkgforge/metadata/tree/main/external/appimagehub/scripts](https://github.com/pkgforge/metadata/tree/main/external/appimagehub/scripts)
* [x] Metadata: [https://meta.pkgforge.dev/external/appimagehub/](https://meta.pkgforge.dev/external/appimagehub/)
{% endhint %}

***

### Add

{% hint style="info" %}
[Using <mark style="color:orange;">**`soar defconfig`**</mark>](#user-content-fn-2)[^2] (<mark style="color:green;">**Recommended**</mark>)

{% code overflow="wrap" %}
```bash
#ONLY If you didn't already use it or have your own custom config
soar defconfig --external
soar sync
soar list 'appimagehub'
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

* [x] Add the repo config (For aarch64: Replace **x86\_64-Linux** with **aarch64-Linux**)

{% code overflow="wrap" %}
```toml
[[repositories]]
name = "appimagehub"
url = "https://meta.pkgforge.dev/external/appimagehub/x86_64-Linux.json.zstd"
```
{% endcode %}

* [x] Sync metadata

{% code overflow="wrap" %}
```bash
soar sync
soar list 'appimagehub'
```
{% endcode %}
{% endhint %}

{% hint style="info" %}
[Using tee](#user-content-fn-4)[^4] (<mark style="color:red;">**NOT-Recommended**</mark>)

* [x] Append (For aarch64: Replace **x86\_64-Linux** with **aarch64-Linux**)

{% code overflow="wrap" %}
```bash
mkdir -pv "~/.config/soar" &&\
tee -a "~/.config/soar/config.toml" <<EOF
[[repositories]]
name = "appimagehub"
url = "https://meta.pkgforge.dev/external/appimagehub/x86_64-Linux.json.zstd"
EOF
```
{% endcode %}

* [x] Sync metadata

{% code overflow="wrap" %}
```bash
soar sync
soar list 'appimagehub'
```
{% endcode %}
{% endhint %}

[^1]: The data is quite poor & requires too much work for us to provide prebuilt cache

[^2]: Assuming you didn't run this before and you DO NOT have your own custom config at <mark style="color:orange;">**`~/.config/soar/config.toml`**</mark>

[^3]: Should use if using custom config or the above command fails

[^4]: Should only use if you can't use a text editor or want to do it non-interactively
