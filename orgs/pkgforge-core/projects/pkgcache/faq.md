---
icon: message-question
description: Frequently Asked Questions & Misc
---

# FAQ

### Broken & Not Portable Packages

* [x] If you find a [**`$PKG`**](../../../../formats/packages/) that doesn't work (<mark style="color:red;">**`segfaults/crashes`**</mark>) or some other <mark style="color:red;">**errors**</mark>, it **will be treated as a bug**.
* [x] First, try to diagnose, and see if it only affects you.
* [x] Also search online and [in the Issues Page](https://github.com/pkgforge/pkgcache/issues), if there are entries about your Issue.

{% hint style="success" %}
- [x] Also, read the relevant entry of your format to see if it's an Edge Case

> * [**$PKG.AppBundle**](https://docs.pkgforge.dev/formats/packages/appbundle#quirks)
> * [**$PKG.AppImage**](https://docs.pkgforge.dev/formats/packages/appimage#quirks)
> * **$PKG.Archives**
> * [**$PKG.FlatImage**](https://docs.pkgforge.dev/formats/packages/flatimage#quirks)
> * **$PKG.GameImage**
> * [**$PKG.NixAppImage**](https://docs.pkgforge.dev/formats/packages/nixappimage#quirks)
> * **$PKG.RunImage**
{% endhint %}

* [x] Finally, [create an Issue](https://github.com/pkgforge/pkgcache/issues/new) (Include as much info as possible, including your [Distro](https://distrowatch.com/), [Desktop Environments](https://en.wikipedia.org/w/index.php?title=Desktop_environment#Gallery), [Window Managers](https://wiki.archlinux.org/title/Window_manager), [XDG\_ENV](https://wiki.archlinux.org/title/XDG_Base_Directory), \[ENV\_VARS (env)]

***

### **Setup & Configure Local Build Environment** <a href="#setup-and-configure-local-build-environment" id="setup-and-configure-local-build-environment"></a>

1. This uses the same Runners & Build Environment as [**Toolpacks (BinCache)**](https://docs.pkgforge.dev/orgs/pkgforge-core/projects/toolpacks-bincache/faq#setup-and-configure-local-build-environment)
2. Initial steps are same, but you will also have to have a [Hugging Face Token](https://huggingface.co/docs/hub/en/security-tokens), check [setup\_env.sh](https://github.com/pkgforge/pkgcache/blob/main/.github/scripts/x86_64-Linux/env.sh) for details

***

### **Why not host on GitHub?**

1. Because GitHub has very conservative limits: [https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github)
2. [Hugging Face](https://huggingface.co/pricing) has [generous limits](https://huggingface.co/docs/hub/en/repositories-recommendations) & [inbuilt support for LFS](https://huggingface.co/docs/hub/en/repositories-getting-started)
3. Last but not least, to avoid [https://docs.pkgforge.dev/orgs/pkgforge-core/projects/pkgcache/dmca-or-copyright-cease-and-desist](https://docs.pkgforge.dev/orgs/pkgforge-core/projects/pkgcache/dmca-or-copyright-cease-and-desist)

***

### Public Tools Search

* [**GitHub Search**](https://github.com/search?q=is%3Apublic+archived%3Afalse+template%3Afalse++stars%3A%3E5+GUI+OR+Portable+OR+Package\&type=repositories\&s=updated\&o=desc): <mark style="color:orange;">`is:public archived:false template:false  stars:>5 GUI OR Portable OR Package`</mark> (**Sorted By**: <mark style="color:purple;">`Recently Updated`</mark>)
* **List**: [https://github.com/stars/Azathothas/lists/soarpkgs-tba](https://github.com/stars/Azathothas/lists/soarpkgs-tba)

***

### Public Code Search

* [**GitHub Search**](https://github.com/search?q=NOT+user%3AAzathothas+NOT+user%3Axplshn+NOT+user%3Ametis-os+NOT+user%3Apkgforge+NOT+user%3Apkgforge-community+NOT+user%3Apkgforge-dev+NOT+user%3Apkgforge-security+NOT+is%3Afork+pkgforge.dev\&type=code): <mark style="color:orange;">`NOT user:Azathothas NOT user:xplshn NOT user:metis-os NOT user:pkgforge NOT user:pkgforge-community NOT user:pkgforge-dev NOT user:pkgforge-security NOT is:fork pkgforge.dev`</mark>
* [**Google**](https://www.google.com)**|**[**Bing**](https://www.bing.com/)**|**[**Baidu**](https://www.baidu.com): <mark style="color:orange;">`"*pkgforge.dev" -site:pkgforge.dev -site:ajam.dev`</mark>

***

### History & Lore

* [**@Azathothas**](https://docs.pkgforge.dev/orgs/pkgforge-core/people#azathothas) drafted repos & projects which would eventually become [Toolpacks](https://github.com/Azathothas/Toolpacks),  \~ **July, 2023**, You can read more about it here: [https://docs.pkgforge.dev/orgs/pkgforge-core/projects/toolpacks-bincache/faq#history-and-lore](https://docs.pkgforge.dev/orgs/pkgforge-core/projects/toolpacks-bincache/faq#history-and-lore)
* Life was fun & everything was okay until: [Azathothas/Toolpacks#28](https://github.com/Azathothas/Toolpacks/issues/28), this made [**@Azathothas**](https://docs.pkgforge.dev/orgs/pkgforge-core/people#azathothas)  go down a rabbit hole where he discovered formats like: [AppBundles](https://github.com/xplshn/pelf/) `|` [AppImages](https://github.com/ivan-hc/AM) `|` [FlatImages](https://github.com/ruanformigoni/flatimage) `|` [RunImages](https://github.com/VHSgunzo)
* Those didn't really fit the theme of [Toolpacks,](https://docs.pkgforge.dev/orgs/pkgforge-core/projects/toolpacks-bincache/differences) and thus this repo came into Existence **\~ Sep 25, 2024** , later it served as an ingestor, after [**SoarPkgs**](https://docs.pkgforge.dev/orgs/pkgforge-core/projects/soarpkgs/faq#history-and-lore) [`~ Nov 04, 2024`](https://github.com/pkgforge/soarpkgs/commit/47b3023010232dfe8b13a83a1daa688e57aa21f1)
