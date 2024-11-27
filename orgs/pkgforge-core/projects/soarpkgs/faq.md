---
icon: message-question
description: Frequently Asked Questions & Misc
---

# FAQ

### **Why not contribute Upstream?**

1. Unfortunately, with the [mass adoption of Flatpaks](https://flatpak.org/), most developers have no interest in AppImages or [other formats](../../../../formats/packages/)
2. The few who do, either lack the interest, skill or time, or all of these to provide a properly made Portable Package. There are numerous examples, you simply need to see their issues tab & search our usernames.
3. So, creating PR that the upstream won't even accept is a huge waste of our time. However, we (mostly [**@Samueru-sama**](https://docs.pkgforge.dev/orgs/pkgforge-dev/people#samueru-sama)) still try our best to contribute upstream whenever possible.

***

### **Why not contribute to AM?** <a href="#setup-and-configure-local-build-environment" id="setup-and-configure-local-build-environment"></a>

1. [**AM**](https://github.com/ivan-hc/AM) is a giant beast, & is entirely in shell. This makes it very hard, if not impossible, to create **CLI**s/**GUI**s in a real programming language, as **there's no programmatic data format like JSON/YAML. Parsing strings from shell scripts is neither safe nor reliable.**
2. The author also believes, it's better to rely on/contribute to upstream, even if upstream has no interest or provides broken packages. You can read, why we disagree: [#why-not-contribute-upstream](faq.md#why-not-contribute-upstream "mention")
3. [**Soar**](https://github.com/pkgforge/soar) prioritizes security through its implementation in Rust, a memory-safe programming language. We are committed to maintaining rigorous security standards, including c**omprehensive build logs**, **robust checksum validation**, and s**ecure build and installation sandboxes**. These protective measures are **fundamental to our approach and non-negotiable**.
4. A safer, saner, easier & richer alternative to hacky-shell script was created, it's called [<mark style="color:purple;">**`SBUILD`**</mark>](broken-reference), You can read about it here: [https://docs.pkgforge.dev/sbuild/introduction](https://docs.pkgforge.dev/sbuild/introduction)

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
* After [Azathothas/Toolpacks#28](https://github.com/Azathothas/Toolpacks/issues/28), [PkgCache](https://docs.pkgforge.dev/orgs/pkgforge-core/projects/pkgcache) was created **\~ Sep 25, 2024**, You can read more about it here: [https://docs.pkgforge.dev/orgs/pkgforge-core/projects/pkgcache/faq#history-and-lore](https://docs.pkgforge.dev/orgs/pkgforge-core/projects/pkgcache/faq#history-and-lore)
* We realized it pretty quickly that, [PkgCache](https://docs.pkgforge.dev/orgs/pkgforge-core/projects/pkgcache) wasn't sustainable, and a User Repository consisting of community submitted packages, just like [**ivan-hc/AM**](https://github.com/ivan-hc/AM), was desperately needed. Thus, [Soarpkgs](https://github.com/pkgforge/soarpkgs), came into existence [`~ Nov 04, 2024`](https://github.com/pkgforge/soarpkgs/commit/47b3023010232dfe8b13a83a1daa688e57aa21f1)
