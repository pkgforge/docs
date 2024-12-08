---
icon: list-tree
description: All the Package Managers that were considered, rejected & selected
---

# 1. Candidates

### Criteria

{% hint style="warning" %}
The following Caveats were applied:

* [x] Must NOT be [**associated with a mainstream distro**](#user-content-fn-1)[^1] (Excluded: [AUR](https://wiki.archlinux.org/title/Arch_User_Repository), [GURU](https://wiki.gentoo.org/wiki/Project:GURU), [NUR](https://nur.nix-community.org/) etc.)
* [x] Must have an active development, i.e. **no abandonware**
* [x] Must have it's own [recipe repository](#user-content-fn-2)[^2] with at least **500 Packages** & NOT use/rely on a [third-party repository](#user-content-fn-3)[^3]
* [x] We included the top 4 (5) Projects that met the above criteria & had the most number of packages
{% endhint %}

***

### Considered

{% hint style="info" %}
<mark style="color:blue;">**Date**</mark>: <mark style="color:orange;">**`2024-12-08`**</mark>

<mark style="color:red;">**Elimination**</mark>: Anything <mark style="color:orange;">**below 10 stars**</mark> was ignored & as well <mark style="color:orange;">**archived repos**</mark>. Anything that has not received any update in the last <mark style="color:orange;">**\~ 2 Years**</mark> was also Ignored.&#x20;

We ended up with:

* https://github.com/babarot/afx
* https://github.com/ivan-hc/AM (https://github.com/ivan-hc/AppMan)
* https://github.com/cosmic-utils/app-hub
* https://github.com/prateekmedia/appimagepool
* https://github.com/AppImageCrafters/appimage-cli-tool
* https://github.com/marcosnils/bin
* https://github.com/rjbrown57/binman
* https://github.com/anchore/binny
* https://github.com/mitchweaver/bonsai
* https://github.com/pegvin/bread
* https://github.com/brioche-dev/brioche
* https://github.com/vinifmor/bauh
* https://github.com/cask-pkg/cask.rs
* https://github.com/xplshn/dbin
* https://github.com/mijorus/gearlever
* https://github.com/dominiksalvet/gitpack
* https://github.com/aerys/gpm
* https://github.com/innobead/huber
* https://github.com/Rishang/install-release
* https://github.com/txthinking/nami
* https://github.com/zyrouge/pho
* https://github.com/leleliu008/ppkg
* https://github.com/marwanhawari/stew
* https://github.com/Alessandro-Salerno/tarman
* https://github.com/srevinsaju/zap
{% endhint %}

***

### Rejected

{% hint style="danger" %}
* **babarot/afx**
{% endhint %}

***

### Selected

{% hint style="success" %}
* [x] [<mark style="color:purple;">**ivan-hc/AM**</mark>](https://github.com/ivan-hc/AM): Meets all the criteria & has it's own [recipe repo](https://github.com/ivan-hc/AM/tree/main/programs)
* [x] [<mark style="color:purple;">**HomeBrew**</mark>](https://brew.sh/): **Far exceeds** all the criteria & has it's own [recipe repo](https://github.com/Homebrew/homebrew-core/tree/master/Formula)
* [x] [<mark style="color:purple;">**Pacstall**</mark>](https://github.com/pacstall/pacstall): Meets all the criteria & has it's own [recipe repo](https://github.com/pacstall/pacstall-programs)
* [x] [<mark style="color:purple;">**leleliu008/ppkg**</mark>](https://github.com/leleliu008/ppkg): Meets all the criteria & has it's own [recipe repo](https://github.com/leleliu008/ppkg-formula-repository-official-core/tree/master/formula/linux)
* [x] [<mark style="color:green;">**pkgforge/soar**</mark>](https://github.com/pkgforge/soar): Well.. We don't need to explain this... do we??
{% endhint %}

[^1]: We allowed [Pacstall](https://github.com/pacstall/pacstall), as it's a community project & NOT backed by any distro. We could have included the [NUR](https://github.com/nix-community/NUR) too, but we already have [homebrew](https://brew.sh/) for reality checks...

[^2]: A central repo containing all the build scripts (recipes)



[^3]: Not controlled/managed by the package manager's authors
