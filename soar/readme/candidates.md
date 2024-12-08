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
* [x] Must have it's own [recipe repository](#user-content-fn-2)[^2] with at least **500 Packages** & NOT use/rely on a [third-party repository](#user-content-fn-3)[^3]. Learn why we mandate a recipe repository instead of using existing ones at: [https://docs.pkgforge.dev/orgs/readme-1/projects/soarpkgs/faq](https://docs.pkgforge.dev/orgs/readme-1/projects/soarpkgs/faq)
* [x] We included the top 4 (5) Projects that met the above criteria & had the most number of packages
{% endhint %}

***

### Considered

{% hint style="info" %}
<mark style="color:blue;">**Date**</mark>: [<mark style="color:orange;">**`2024-12-08`**</mark>](#user-content-fn-4)[^4]

<mark style="color:red;">**Elimination**</mark>: Anything <mark style="color:orange;">**below 10 stars**</mark> was ignored & as well <mark style="color:orange;">**archived repos**</mark>. Anything that has not received any update in the last <mark style="color:orange;">**\~ 2 Years**</mark> was also Ignored.&#x20;

We ended up with:

* <mark style="color:blue;">https://github.com/babarot/afx</mark>
* <mark style="color:blue;">https://github.com/ivan-hc/AM (https://github.com/ivan-hc/AppMan)</mark>
* <mark style="color:blue;">https://github.com/cosmic-utils/app-hub</mark>
* <mark style="color:blue;">https://github.com/prateekmedia/appimagepool</mark>
* <mark style="color:blue;">https://github.com/AppImageCrafters/appimage-cli-tool</mark>
* <mark style="color:blue;">https://github.com/marcosnils/bin</mark>
* <mark style="color:blue;">https://github.com/rjbrown57/binman</mark>
* <mark style="color:blue;">https://github.com/anchore/binny</mark>
* <mark style="color:blue;">https://github.com/mitchweaver/bonsai</mark>
* <mark style="color:blue;">https://github.com/pegvin/bread</mark>
* <mark style="color:blue;">https://github.com/brioche-dev/brioche</mark>
* <mark style="color:blue;">https://github.com/vinifmor/bauh</mark>
* <mark style="color:blue;">https://github.com/cask-pkg/cask.rs</mark>
* <mark style="color:blue;">https://github.com/xplshn/dbin</mark>
* <mark style="color:blue;">https://github.com/mijorus/gearlever</mark>
* <mark style="color:blue;">https://github.com/dominiksalvet/gitpack</mark>
* <mark style="color:blue;">https://github.com/aerys/gpm</mark>
* <mark style="color:blue;">https://github.com/innobead/huber</mark>
* <mark style="color:blue;">https://github.com/Rishang/install-release</mark>
* <mark style="color:blue;">https://github.com/txthinking/nami</mark>
* <mark style="color:blue;">https://github.com/zyrouge/pho</mark>
* <mark style="color:blue;">https://github.com/leleliu008/ppkg</mark>
* <mark style="color:blue;">https://github.com/marwanhawari/stew</mark>
* <mark style="color:blue;">https://github.com/srevinsaju/zap</mark>
{% endhint %}

***

### Rejected

{% hint style="danger" %}
* [**babarot/afx**](https://github.com/babarot/afx) : No Recipe Repository & Likely <mark style="color:orange;">**Abandoned**</mark>
* [**cosmic-utils/app-hub**](https://github.com/cosmic-utils/app-hub):  [No Recipe Repository](https://github.com/cosmic-utils/app-hub/issues/68)
* [**prateekmedia/appimagepool**](https://github.com/prateekmedia/appimagepool): [No Recipe Repository](https://github.com/prateekmedia/appimagepool/blob/a7db55eaa554f144eb30bf89732f2abf4e9068f5/lib/src/features/home/presentation/home/home_page.dart#L89) (Uses [appimage.github.io](https://github.com/AppImage/appimage.github.io)) & Likely <mark style="color:orange;">**Abandoned**</mark>
* [**AppImageCrafters/appimage-cli-tool**](https://github.com/AppImageCrafters/appimage-cli-tool): Included here, just for brevity[^5]. <mark style="color:orange;">**Completely Abandoned**</mark>
* [**marcosnils/bin**](https://github.com/marcosnils/bin): [Too few "official" recipes](https://github.com/marcosnils/bin/wiki/Tools-list), mostly just another [eget](https://github.com/zyedidia/eget) clone with Package Management
* [**rjbrown57/binman**](https://github.com/rjbrown57/binman): No Recipe Repository & just another [eget](https://github.com/zyedidia/eget) clone with Package Management
* [**anchore/binny**](https://github.com/anchore/binny): No Recipe Repository & just another [eget](https://github.com/zyedidia/eget) clone with Package Management
* [**mitchweaver/bonsai**](https://github.com/mitchweaver/bonsai): [Too few "official" recipes](https://github.com/mitchweaver/bonsai/tree/master/ports)
* [**pegvin/bread**](https://github.com/pegvin/bread): [No Recipe Repository](https://github.com/pegvin/bread/blob/7740933b3e23c26499dcf9711656913b0e25245b/README.md?plain=1#L143)  (Uses [appimage.github.io](https://github.com/AppImage/appimage.github.io)) & Likely <mark style="color:orange;">**Abandoned**</mark>
* [**brioche-dev/brioche**](https://github.com/brioche-dev/brioche): [Too few "official" recipes](https://github.com/brioche-dev/brioche-packages/tree/main/packages)
* [**vinifmor/bauh**](https://github.com/vinifmor/bauh): [No Recipe Repository](https://github.com/vinifmor/bauh-files/blob/f50d6f98d76671979bf79a801109386a2e387d1e/README.md?plain=1#L6) (Uses [appimage.github.io](https://github.com/AppImage/appimage.github.io)). This is actually the only one actively maintained appimage manager with a GUI. We <mark style="color:green;">recommend</mark> it, but we will reject it as it doesn't meet our [criteria](candidates.md#criteria)
* [**cask-pkg/cask.rs**](https://github.com/cask-pkg/cask.rs): [Too few "official" recipes](https://github.com/cask-pkg/cask-core/tree/main/github.com)
* [**xplshn/dbin**](https://github.com/xplshn/dbin): [Too few "official" recipes](https://github.com/xplshn/AppBundleHUB/tree/97baefdcc7ef73b1a2525dd33a888b19046bc023/recipes) & these are [xplshn's own format](https://github.com/xplshn/pelf).  (Uses [pkforge's metadata](https://github.com/xplshn/dbin/blob/ed3475a4f66a46d6cb4d9dd1ff3942ae6246e8da/README.md?plain=1#L136)).  This is actually the only one actively maintained package manager with [lots of packages](https://github.com/xplshn/dbin/blob/ed3475a4f66a46d6cb4d9dd1ff3942ae6246e8da/misc/assets/counter.svg). We <mark style="color:green;">recommend</mark> it, but we will reject it as it doesn't meet our [criteria](candidates.md#criteria)
* [**mijorus/gearlever**](https://github.com/mijorus/gearlever): No Recipe Repository, needs local file
* [**dominiksalvet/gitpack**](https://github.com/dominiksalvet/gitpack): Not a regular package manager; Works with Git Repos, but the repos must have a special dir to support it
* [**aerys/gpm**](https://github.com/aerys/gpm): Not a regular package manager; Works with Git Repos, but requires LFS & other extra steps
* [**innobead/huber**](https://github.com/innobead/huber): No Recipe Repository & just another [eget](https://github.com/zyedidia/eget) clone with Package Management
* [**Rishang/install-release**](https://github.com/Rishang/install-release): No Recipe Repository & just another [eget](https://github.com/zyedidia/eget) clone with Package Management
* [**txthinking/nami**](https://github.com/txthinking/nami): [Too few "official" recipes](https://github.com/txthinking/nami/tree/master/package)
* [**zyrouge/pho**](https://github.com/zyrouge/pho): No Recipe Repository & just another [eget](https://github.com/zyedidia/eget) clone but for AppImage only
* [**marwanhawari/stew**](https://github.com/marwanhawari/stew): No Recipe Repository & just another [eget](https://github.com/zyedidia/eget) clone with Package Management
* [**srevinsaju/zap**](https://github.com/srevinsaju/zap): [No Recipe Repository](https://github.com/srevinsaju/zap/blob/ef44059447ebcbe83019136269b325ff9d79d4ab/README.md?plain=1#L67) (Uses [appimage.github.io](https://github.com/AppImage/appimage.github.io)) & Likely <mark style="color:orange;">**Abandoned**</mark>
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

[^4]: In case any of the information changes later

[^5]: It is kind of "official"

