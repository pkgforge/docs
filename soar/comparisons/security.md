---
icon: lock
description: Security Postures
---

# 4. Security

{% hint style="info" %}
**Before proceeding, we&#x20;**<mark style="color:green;">**recommend**</mark>**&#x20;reading**:&#x20;

* [x] [https://docs.pkgforge.dev/repositories/pkgforge-edge/security](https://docs.pkgforge.dev/repositories/pkgforge-edge/security)
* [x] [https://docs.pkgforge.dev/repositories/pkgforge-community/security](https://docs.pkgforge.dev/repositories/pkgforge-community/security)
{% endhint %}

***

<table data-header-hidden data-full-width="false"><thead><tr><th>Package Manager</th><th>Build/Install (Privileged)?</th><th>Build/Install (Sandboxed)?</th><th>Build/Install (Validation)?</th></tr></thead><tbody><tr><td><a href="https://github.com/ivan-hc/AM/tree/main/programs"><mark style="color:purple;"><strong><code>AM</code></strong></mark></a></td><td><a data-footnote-ref href="#user-content-fn-1"><mark style="color:orange;"><strong>Depends</strong></mark></a></td><td></td><td></td></tr><tr><td><a href="https://brew.sh/"><strong><code>Brew</code></strong></a></td><td><strong>No</strong></td><td><a href="https://github.com/Homebrew/brew/search?l=ruby">ruby</a> + <a href="https://github.com/Homebrew/brew/search?l=shell">bash</a></td><td></td></tr><tr><td></td><td></td><td></td><td></td></tr><tr><td><a href="https://github.com/pacstall"><strong><code>Pacstall</code></strong></a></td><td><strong>Yes</strong> (See <a href="https://github.com/pacstall/pacstall/blob/0b9659f5bb28de8fbcd921346619385a24199024/install.sh#L89">#Installation</a>)</td><td><a href="https://github.com/pacstall/pacstall/search?l=shell">bash</a></td><td><a href="https://github.com/pacstall/pacstall/blob/0b9659f5bb28de8fbcd921346619385a24199024/install.sh#L59"><strong>Yes</strong></a></td></tr><tr><td><a href="https://github.com/leleliu008/ppkg"><strong><code>PPKG</code></strong></a></td><td><strong>Yes</strong> (See <a href="https://github.com/leleliu008/ppkg/blob/ec2f8757f94776a0fe6c116c90ac18eddc21ef14/ppkg#L8574">#Installation</a>)</td><td><a href="https://github.com/leleliu008/ppkg/search?l=shell">bash</a> + <a href="https://github.com/leleliu008/ppkg/search?l=c">c</a></td><td><a href="https://github.com/leleliu008/ppkg/blob/ec2f8757f94776a0fe6c116c90ac18eddc21ef14/ppkg#L8823"><strong>Yes</strong></a></td></tr><tr><td><a href="https://github.com/pkgforge/soar"><strong><code>Soar</code></strong></a></td><td></td><td><a href="https://github.com/pkgforge/soar/search?l=rust">rust</a></td><td></td></tr></tbody></table>



[^1]: AM runs all build script with <mark style="color:red;">**sudo**</mark>\
    AppMan runs it as current user
