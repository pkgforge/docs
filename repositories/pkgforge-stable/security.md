---
icon: shield-quartered
description: It is NEVER a good idea to install random binaries from random sources.
---

# Security

### Recommended Reading

{% hint style="info" %}
Check these **`HackerNews Discussions`**

* [x] [https://blogs.gentoo.org/mgorny/2021/02/19/the-modern-packagers-security-nightmare/](https://blogs.gentoo.org/mgorny/2021/02/19/the-modern-packagers-security-nightmare/) (HN: [https://news.ycombinator.com/item?id=26203853](https://news.ycombinator.com/item?id=26203853))
* [x] [A cautionary tale from the decline of SourceForge](https://news.ycombinator.com/item?id=31110206)
* [x] [Downloading PuTTY Safely Is Nearly Impossible (2014)](https://news.ycombinator.com/item?id=9577861)
* [x] [Post-xz backdoor, how to know when to trust niche-distro binaries?](https://www.reddit.com/r/DistroHopping/comments/1bu5mri/postxz_backdoor_how_to_know_when_to_trust/)
* [x] A number of FAQs were also answered when [Hysp (Frontend PKG Manager)](https://github.com/pwnwriter/hysp) was [featured on HN](https://news.ycombinator.com/item?id=38457926): [https://news.ycombinator.com/item?id=38457926](https://news.ycombinator.com/item?id=38457926)
{% endhint %}

* [x] [The XZ Backdoor](https://gist.github.com/thesamesam/223949d5a074ebc3dce9ee78baad9e27)
* [x] [Reproducible Builds](https://reproducible-builds.org/docs/definition/)

{% hint style="warning" %}
The amount of work and the near impossibility to ensure that every source used, provide reproducibility, is infeasibly impractical. Even if it were practical, not every `pkg/tool` provides source code, so this is impractical.
{% endhint %}

***

### Trust but Verify

* [x] All the Build Scripts & workflows are completely open-source. You are free to audit & scrutinize everything.

{% hint style="info" %}
- [x] You can view <mark style="color:orange;">**RAW Build Script**</mark>

```bash
!# View Build Script
soar inspect "<PACKAGE>"
```
{% endhint %}

{% hint style="warning" %}
if you get a 404 or it errors out, you can get the build script here: [https://github.com/pkgforge/soarpkgs/tree/main/packages](https://github.com/pkgforge/soarpkgs/tree/main/packages)
{% endhint %}

* [x] Complete `RAW` **Build Logs** are made available with the **exception of `Personal Access Tokens`**

{% hint style="info" %}
- [x] You can view <mark style="color:orange;">**RAW Build Logs**</mark>

```bash
!# View Logs
soar log "<PACKAGE>"
```
{% endhint %}

{% hint style="warning" %}
If you get a 404 or it errors out, you can get the full logs for [**Toolpacks (BinCache)**](https://docs.pkgforge.dev/orgs/pkgforge-core/projects/toolpacks-bincache) here:

* [x] <mark style="color:orange;">**`aarch64-Linux`**</mark> :  [https://bin.pkgforge.dev/aarch64/BUILD.log.txt ](https://bin.pkgforge.dev/aarch64/BUILD.log.txt)
* [x] <mark style="color:orange;">**`x86_64-Linux`**</mark> :  [https://bin.pkgforge.dev/x86\_64/BUILD.log.txt ](https://bin.pkgforge.dev/x86_64/BUILD.log.txt)
{% endhint %}

{% hint style="warning" %}
If you get a 404 or it errors out, you can get the full logs for [**PkgCache**](https://docs.pkgforge.dev/orgs/pkgforge-core/projects/pkgcache) here:

* [x] <mark style="color:orange;">**`aarch64-Linux`**</mark> :  [https://pkg.pkgforge.dev/aarch64/BUILD.log.txt ](https://pkg.pkgforge.dev/aarch64/BUILD.log.txt)
* [x] <mark style="color:orange;">**`x86_64-Linux`**</mark> :  [https://pkg.pkgforge.dev/x86\_64/BUILD.log.txt](https://pkg.pkgforge.dev/x86_64/BUILD.log.txt)&#x20;
{% endhint %}

* [x] Both <mark style="color:orange;">**`SHA256SUM`**</mark> & <mark style="color:orange;">**`BLAKE3SUM`**</mark> are automatically generated right after build script finishes.

{% hint style="warning" %}
**Since, the builds aren't reproducible, it's unlikely you will end up with the same checksums if you rebuild/rerun the Build Script**
{% endhint %}

* [x] If it still doesn't inspire confidence, there's a [Docker Image](https://docs.pkgforge.dev/orgs/pkgforge-core/projects/toolpacks-bincache/faq#setup-and-configure-local-build-environment) you can Configure to Run & Reproduce any Binary/Build Script on your own Secure System.

> - **Dockerfiles**: [https://github.com/Azathothas/Toolpacks/tree/main/.github/runners](https://github.com/Azathothas/Toolpacks/tree/main/.github/runners)
> - [https://github.com/pkgforge/pkgcache/tree/main/.github/scripts](https://github.com/pkgforge/pkgcache/tree/main/.github/scripts)

***

### Don't Trust Us

1. Repos that already publish pre-compiled binaries/packages, nothing is changed. You can **compare checksums**.

{% hint style="warning" %}
* For [Binaries](../../formats/binaries/), Debug Symbols, Comments are stripped, this will change the checksum
* For [Packages](../../formats/packages/), Icons, Desktops (& even repacking) are edited/fixed & patched, this will change the checksum&#x20;
* **To preserve checksums wherever possible, we don't sign any of our binaries as we already have Logs + Checksums**
{% endhint %}

2. Fork our repos, read & audit our code, setup all the infrastructure, & run all the scripts & build on your own servers

***

### Spooky Things

{% hint style="danger" %}
Follow this guide to analyze a malicious binary/package: [https://book.hacktricks.xyz/generic-methodologies-and-resources/basic-forensic-methodology/malware-analysis](https://book.hacktricks.xyz/generic-methodologies-and-resources/basic-forensic-methodology/malware-analysis)
{% endhint %}

1. First, it's important to verify that the alert is [NOT a False Positive](https://web.archive.org/web/2/https://www.majorgeeks.com/content/page/how_to_tell_the_difference_between_a_virus_and_a_false_positive.html) and **truly confirm** that indeed the [Binary is Malicious](https://www.reddit.com/r/linux4noobs/comments/18pbfv1/how_can_i_determine_a_elf_executable_is_malicious/)
2. Second, check the affected Binary's Build Script, the latest BUILD.log & finally CHECKSUMS as described in above sections.
3. Third, if you find everything is as it should be, **create an Issue** & **attach&#x20;**<mark style="color:orange;">**Verifiable**</mark>**&#x20;and&#x20;**<mark style="color:red;">**Reproducible Proof**</mark>.

{% hint style="danger" %}
It's important to NOTE that **WE DO NOT WRITE/OWN the binaries we compile and CAN NOT BE HELD RESPONSIBLE if the Developer has DELIBERATELY made it Malicious**. If that's the case, it's best to **Notify Us (Create an Issue OR** [**Contact Us**](https://docs.pkgforge.dev/contact)**) & also** [**Report To Github the Original Repo**](https://docs.github.com/en/communities/maintaining-your-safety-on-github/reporting-abuse-or-spam) like here: [https://github.com/orgs/community/discussions/63603](https://github.com/orgs/community/discussions/63603)
{% endhint %}

4. All the [Build Servers](../pkgforge-edge/infra.md) follow [Standard Security Hardening](https://docs.github.com/en/actions/security-for-github-actions/security-guides/security-hardening-for-github-actions) to mitigate [Supply Chain Attacks](https://docs.github.com/en/code-security/supply-chain-security/understanding-your-software-supply-chain/about-supply-chain-security), so a single Malicious Binary is more probable than ALL the binaries being infected.
5. Once again, to reiterate, **the source code of the packages or tools compiled here is not controlled in any way.**&#x20;

{% hint style="danger" %}
It cannot be guaranteed that the upstream source is entirely safe or legitimate. It's upto you to exercise basic common sense and vigilance when using these binaries/packages.
{% endhint %}
