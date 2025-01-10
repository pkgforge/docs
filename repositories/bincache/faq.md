---
icon: message-question
description: Frequently Asked Questions & Misc
---

# FAQ

{% hint style="info" %}
Some questions may have already been addressed at: [https://docs.pkgforge.dev/repositories/soarpkgs/faq](https://docs.pkgforge.dev/repositories/soarpkgs/faq)

Also at: [https://docs.pkgforge.dev/repositories/pkgcache/faq](https://docs.pkgforge.dev/repositories/pkgcache/faq)
{% endhint %}

***

### Toolpacks

Toolpacks was (now archived) the old repo where majority of static binaries' build scripts were hosted.\
It was archived on <mark style="color:orange;">`2025-01-01`</mark> as part of [a massive rewrite](https://github.com/pkgforge/bincache/issues/1), you can read more at [#history-and-lore](faq.md#history-and-lore "mention")

### Android Deprecation

{% hint style="warning" %}
Android Support was deprecated on [**`Nov 18, 2024`**](https://github.com/Azathothas/Toolpacks/issues/38#issuecomment-2482936345)  (Toolpacks)
{% endhint %}

1. Android is [weird & very different from Linux](https://wiki.termux.com/wiki/Differences_from_Linux).
2. Android has [known issues that are **won't fix | by design**](https://github.com/termux/termux-packages/wiki/Common-porting-problems)
3. Android binaries [**CAN NOT BE COMPILED STATICALLY**](https://github.com/Zackptg5/Cross-Compiled-Binaries-Android/tree/master/build_script#dns-issues) without significant efforts & manual patching for each & every binary. This is not Automatable.
4. [bin.pkgforge.dev/arm64\_v8a\_Android](https://bin.pkgforge.dev/arm64_v8a_Android/) only ever provided Tools/Pkgs (Only for **`arm64-v8a`**) that  [**@Azathothas**](https://docs.pkgforge.dev/orgs/pkgforge-core/people#azathothas) personally used to use but which weren't already available in [**termux-pkgs**](https://github.com/Azathothas/Termux-Packages) or broken.
5. [**Termux**](https://termux.dev/en/) already [**ports thousands of packages**](https://github.com/termux/termux-packages)**,** Check the [Issues for your `pkg`](https://github.com/termux/termux-packages/issues)**. There's also a near-complete list of all packages officially available on Termux:** [**https://termux-packages.ajam.dev/**](https://termux-packages.ajam.dev/)
6. Check [**@leleliu008**](https://github.com/leleliu008)'s project [**https://github.com/leleliu008/ndk-pkg**](https://github.com/leleliu008/ndk-pkg)**,** if you still don't want to use Termux.

***

### Windows Deprecation

{% hint style="warning" %}
Windows Support was deprecated on [**`Nov 18, 2024`**](https://github.com/Azathothas/Toolpacks/issues/38#issuecomment-2482936345)  (Toolpacks)
{% endhint %}

1. Windows is **centralized** & thus benefits from central App Stores like the [**Windows Store**](https://apps.microsoft.com/home?hl=en-US\&gl=US) & [**WinGet**](https://learn.microsoft.com/en-us/windows/package-manager/winget/)
2. It has some of the same issues, Android has, i.e. can't be fully statically linked.
3. There already exist [<mark style="color:purple;">**UniGetUI**</mark>](https://github.com/marticliment/UniGetUI) , which is a pretty & mature wrapper around [WinGet](https://learn.microsoft.com/en-us/windows/package-manager/), [Scoop](https://scoop.sh/), [Chocolatey](https://chocolatey.org/), [Pip](https://pypi.org/), [Npm](https://www.npmjs.com/), [.NET Tool](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-tool-install), [PowerShell Gallery](https://www.powershellgallery.com/) and [**more**](https://github.com/marticliment/UniGetUI?tab=readme-ov-file#supported-package-managers)

***

### More Architectures & OS

* We would like to build binaries for other architectures like [**`riscv64`**](https://en.wikipedia.org/wiki/RISC-V), and the [BSD Family of OSes](https://en.wikipedia.org/wiki/Comparison_of_BSD_operating_systems), however our time & especially **RESOURCES** are limited.
* If you would like to see additional build targets prioritized, donating a <mark style="color:orange;">**Dedicated Build Server**</mark> would be the optimal encouragement.

{% hint style="warning" %}
- Note: <mark style="color:orange;">`32-Bit`</mark> Binaries will likely never be Supported/Added since that's now ancient and even embedded devices now ship with `64-Bit` **ARCH**
{% endhint %}

***

### History & Lore

{% hint style="success" %}
* This, at the time of writing is, the [**largest collection**](https://pkgs.pkgforge.dev/) of _`downloadable`_ (without requiring compilation) & _`up-to-date`_ [static binaries](https://en.wikipedia.org/wiki/Static_build) available on the public web.
* **`More >`** than all of these _COMBINED_: [andrew-d/static-binaries](https://github.com/andrew-d/static-binaries), [s.minos.io/archive/](https://github.com/minos-org/minos-static), [polaco1782/linux-static-binaries](https://github.com/polaco1782/linux-static-binaries), [borestad/static-binaries](https://github.com/borestad/static-binaries), [files.serverless.industries/bin/](https://github.com/perryflynn/static-binaries), [mosajjal/binary-tools](https://github.com/mosajjal/binary-tools), [ryanwoodsmall/static-binaries](https://github.com/ryanwoodsmall/static-binaries), [bol-van/bins](https://github.com/bol-van/bins)
* All of the projects listed above, served as inspirations at one point, so we thank the authors of these projects from the deepest of our hearts. PkgForge wouldn't exist without their work.
{% endhint %}

[**@Azathothas**](https://docs.pkgforge.dev/orgs/pkgforge-core/people#azathothas) used to be [bug bounty hunter](https://en.wikipedia.org/wiki/Bug_bounty_program), a long time ago in another life. He often had to set up pentesting environments on remote Servers, at that time there used to be [https://github.com/six2dez/reconftw](https://github.com/six2dez/reconftw), which installed a bunch of tools (often installing go/rust just to install the tools), this made the setup time awfully slow & frustrated him.

Eventually, <mark style="color:orange;">**`~ July, 2023`**</mark>, he would start modifying the setup scripts, as well as maintaining some homegrown scripts by himself. In the best of case, it was simply a wrapper around [eget](https://github.com/zyedidia/eget), to just fetch a precompiled binary from GitHub. In the worst of cases, it was installing go/rust toolchains, same as reconftw was doing just to install the tools. So he started creating repos on GitHub to build & release these binaries using GH's CI, and then using eget to pull them. The number of repos grew, and it was harder and harder to maintain each, thus [ToolPacks](https://github.com/Azathothas/Toolpacks/tree/main) (The precursor to all our works) was created to centralize them all. You can find all the several iterations this repository went through over the years, on the [web-archive](https://web.archive.org/web/20240000000000*/https://github.com/Azathothas/Toolpacks). Toolpacks was eventually archived on <mark style="color:orange;">`2025-01-01`</mark> as part of [a massive rewrite](https://github.com/pkgforge/bincache/issues/1).

[**@Azathothas**](https://docs.pkgforge.dev/orgs/pkgforge-core/people#azathothas) recommends reading these articles if you need a technical justification:

* [x] ["Static Linking Considered Harmful" Considered Harmful](https://gavinhoward.com/2021/10/static-linking-considered-harmful-considered-harmful/)
* [x] [Dynamic Linking Is Bad For Apps And Static Linking Is Also Bad For Apps](https://belkadan.com/blog/2022/02/Dynamic-Linking-and-Static-Linking/)
* [x] [Oasis Linux](https://github.com/oasislinux/oasis) & [Anton Samokhvalov](https://github.com/pg83)'s [Stalix](https://stal-ix.github.io/STALIX.html) both are distros specifically using only Static Binaries. Check their project page to learn Why.
* [x] And then we have things like [Cosmopolitan Libc](https://github.com/jart/cosmopolitan) & [T2 SDE](https://t2sde.org/about.html), they are very different from a Static Binary POV, but their rationale for doing so applies to why Static Binaries must exist.

A special mention to [**@pwnwriter**](https://github.com/pwnwriter) who reached out to [**@Azathothas**](https://docs.pkgforge.dev/orgs/pkgforge-core/people#azathothas), and created the very first Package manager [**Hysp**](https://github.com/pwnwriter/hysp) **\~** [`Nov 17, 2023`](https://github.com/pwnwriter/hysp/commits/main/?after=f9f9f3c3933b6ed35f0682bdec91d420430f898e+104) . Sadly,  [**Hysp**](https://github.com/pwnwriter/hysp) was **archived on May 26, 2024**.&#x20;

Another mention to [**@Xplshn**](https://github.com/xplshn) who created a package manager in sh called [**bdl**](https://github.com/xplshn/Handyscripts/blob/master/bdl) [`~ Dec 20, 2023`](https://github.com/xplshn/Handyscripts/commits/master/bdl?after=3505b7757e01d41ea45bc24203a68a0ec0aa9c64+34), which later turned into the Golang [**BigDL**](https://github.com/xplshn/bigdl) [`~ Feb 5, 2024`](https://github.com/xplshn/bigdl/commits/master/?after=f54b3ea0d1465993b97acb8b332c226d307223f6+349), which again turned int**o** [**Dbin**](https://github.com/xplshn/dbin) [`~ Aug 23, 2024`](https://github.com/xplshn/dbin/commit/5ae3f34eb2c3995919c06e14f92750f9802068af).

Seeing all these efforts, and some encouragements on [Lobsters](https://lobste.rs/s/iqxjee/poor_man_s_package_manager_only),  [**@Azathothas**](https://docs.pkgforge.dev/orgs/pkgforge-core/people#azathothas) approached [**@QaidVoid**](https://github.com/QaidVoid) and [**Soar**](https://github.com/pkgforge/soar) received it's first commit on [**`Oct 3, 2024`**](https://github.com/pkgforge/soar/commit/06331f438a35dbb40da868fdc606b71f0272d7d9). One thing led to another, and the [**PkgForge**](https://github.com/pkgforge) Organization came into being on **`Nov 4, 2024`** to do everything _**officially**_ and have more control over the direction of all our projects.
