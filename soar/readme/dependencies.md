---
icon: codepen
description: What's needed to install, run & use these Package Manager
---

# 2. Dependencies

### Installation/Setup

{% hint style="info" %}
Try an experiment:

* [x] Install each of these tools on a minimal debian/alpine image & see how many survive
* [x] Doing so, will tell you exactly what dependencies each need
{% endhint %}

{% hint style="warning" %}
We assume you have **curl/wget** to download a file or at the very least transfer from another system. As such, **we excluded curl/wget** writing as a host dependency
{% endhint %}

<table><thead><tr><th width="189">Package Manager</th><th>Language</th><th>Needs Dependencies on Host?</th><th>Needs doas/sudo?</th></tr></thead><tbody><tr><td><a href="https://github.com/ivan-hc/AM/tree/main/programs"><mark style="color:purple;"><strong><code>AM</code></strong></mark></a></td><td><a href="https://github.com/ivan-hc/AM/search?l=shell">bash</a></td><td><a href="https://github.com/ivan-hc/AM/blob/31b14299c7e255b852fbfc5aa7174a90b12a5b66/README.md?plain=1#L67"><mark style="color:orange;"><strong>Yes</strong></mark></a> (See <a href="https://github.com/ivan-hc/AM#installation">#Installation</a>)</td><td><a data-footnote-ref href="#user-content-fn-1"><mark style="color:orange;"><strong>Depends</strong></mark></a></td></tr><tr><td><a href="https://brew.sh/"><mark style="color:purple;"><strong><code>Brew</code></strong></mark></a></td><td><a href="https://github.com/Homebrew/brew/search?l=ruby">ruby</a> + <a href="https://github.com/Homebrew/brew/search?l=shell">bash</a></td><td><a href="https://docs.brew.sh/Homebrew-on-Linux#requirements"><mark style="color:orange;"><strong>Yes</strong></mark></a> (See <a href="https://github.com/Homebrew/install/blob/master/install.sh">#Installation</a>)</td><td><a data-footnote-ref href="#user-content-fn-2"><mark style="color:red;"><strong>Yes*</strong></mark></a></td></tr><tr><td><a href="https://github.com/pacstall"><mark style="color:purple;"><strong><code>Pacstall</code></strong></mark></a></td><td><a href="https://github.com/pacstall/pacstall/search?l=shell">bash</a></td><td><mark style="color:orange;"><strong>Yes</strong></mark> (See <a href="https://github.com/pacstall/pacstall/blob/0b9659f5bb28de8fbcd921346619385a24199024/install.sh#L89">#Installation</a>)</td><td><a href="https://github.com/pacstall/pacstall/blob/0b9659f5bb28de8fbcd921346619385a24199024/install.sh#L59"><mark style="color:red;"><strong>Yes</strong></mark></a></td></tr><tr><td><a href="https://github.com/leleliu008/ppkg"><mark style="color:purple;"><strong><code>PPKG</code></strong></mark></a></td><td><a href="https://github.com/leleliu008/ppkg/search?l=shell">bash</a> + <a href="https://github.com/leleliu008/ppkg/search?l=c">c</a></td><td><mark style="color:orange;"><strong>Yes</strong></mark> (See <a href="https://github.com/leleliu008/ppkg/blob/ec2f8757f94776a0fe6c116c90ac18eddc21ef14/ppkg#L8574">#Installation</a>)</td><td><a href="https://github.com/leleliu008/ppkg/blob/ec2f8757f94776a0fe6c116c90ac18eddc21ef14/ppkg#L8823"><mark style="color:red;"><strong>Yes</strong></mark></a></td></tr><tr><td><a href="https://github.com/pkgforge/soar"><mark style="color:purple;"><strong><code>Soar</code></strong></mark></a></td><td><a href="https://github.com/pkgforge/soar/search?l=rust">rust</a></td><td><a data-footnote-ref href="#user-content-fn-3"><mark style="color:green;"><strong>None</strong></mark></a></td><td><a data-footnote-ref href="#user-content-fn-4"><mark style="color:green;"><strong>No</strong></mark></a></td></tr></tbody></table>

[^1]: AM has two modes:\
    System Wide AM (Default), this needs doas/sudo\
    User Mode AppMan, this doesn't need doas/sudo

[^2]: The official installed needs sudo, but they also offer the option of downloading the tar & extracting it to a location.\
    At least, they discourage it actively: [https://docs.brew.sh/FAQ#why-does-homebrew-say-sudo-is-bad](https://docs.brew.sh/FAQ#why-does-homebrew-say-sudo-is-bad)

[^3]: You don't even need curl/wget as long as you can copy the static binary



[^4]: No doas/sudo at any time for whatsoever reason.
