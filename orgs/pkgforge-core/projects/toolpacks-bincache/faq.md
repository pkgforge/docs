---
icon: message-question
description: Frequently Asked Questions & Misc
---

# FAQ

### Broken & Not Statically Linked

* [x] If you find a [**binary**](../../../../formats/binaries/) that doesn't work (<mark style="color:red;">**`segfaults/crashes`**</mark>) or is <mark style="color:orange;">**`dynamically linked`**</mark>, it will be **treated as a bug**.
* [x] First, try to diagnose, and see if it only affects you.
* [x] Also search online and [in the Issues Page](https://github.com/pkgforge/pkgcache/issues), if there are entries about your Issue.

{% hint style="warning" %}
1. There's an automated CI which checks for these
2. &#x20;[aarch64-Linux](https://github.com/Azathothas/Toolpacks/blob/main/aarch64-Linux/BUILD_ERROR.log.md) : [https://github.com/Azathothas/Toolpacks/blob/main/aarch64-Linux/BUILD\_ERROR.log.md](https://github.com/Azathothas/Toolpacks/blob/main/aarch64-Linux/BUILD_ERROR.log.md)
3. &#x20;[x86\_64-Linux](https://github.com/Azathothas/Toolpacks/blob/main/x86_64-Linux/BUILD_ERROR.log.md) : [https://github.com/Azathothas/Toolpacks/blob/main/x86\_64-Linux/BUILD\_ERROR.log.md](https://github.com/Azathothas/Toolpacks/blob/main/x86_64-Linux/BUILD_ERROR.log.md)
4. So if it's already there, it will eventually be fixed.
{% endhint %}

* [x] If it's NOT Or you would like us to fix it ASAP, [please create an Issue](https://github.com/Azathothas/Toolpacks/issues/new)

{% hint style="info" %}
- **Title**: Summary of Issue along with <mark style="color:orange;">**`Binary`**</mark> & <mark style="color:blue;">**`Platfrom`**</mark> Name
- **`Description`**: Show the <mark style="color:red;">**`crash/segfault`**</mark> screenshot or provide <mark style="color:orange;">**`file/ldd/readelf`**</mark> output along with what would be the correct behaviour
- **Tag**: <mark style="color:orange;">**`BUG`**</mark> + <mark style="color:blue;">**`$PLATFORM`**</mark>
{% endhint %}

***

### Baseutils

{% hint style="info" %}
Essentially [Baseutils is a collection](https://bin.pkgforge.dev/x86_64_Linux/Baseutils/) of Bins from CoreUtils + BusyBox + FindUtils + OpenSSH + Procps + ToyBox + UtilLinux + XZ-Utils & [`More`](https://bin.pkgforge.dev/x86_64_Linux/Baseutils/). Mostly meant for restricted environments like ephemeral [AWS Lambda](https://medium.com/clog/ssh-ing-into-your-aws-lambda-functions-c940cebf7646), [Google Cloud Functions](https://cloud.google.com/functions?hl=en) or anywhere really where there's a lack of coreutils or no privs to use pkg managers. This could also be _theoretically_ used to [bootstrap a linux distro](https://www.youtube.com/watch?v=0vOEcw_sPaM), however, some binaries may not work as we haven't tested all of them comprehensively. Stability & Reliability isn't Guaranteed.
{% endhint %}

***

### UPX

* Binaries are also packed using [<mark style="color:orange;">**`upx --best`**</mark>](https://github.com/upx/upx/blob/devel/doc/upx-doc.txt#L114) after a [CI Build is Complete.](https://github.com/Azathothas/Toolpacks/actions)
* These can be downloaded by either using <mark style="color:orange;">**`soar add "${BIN}" --prefer-upx`**</mark> or by simply adding a <mark style="color:orange;">**`.upx`**</mark> to any binary.

{% hint style="warning" %}
- There is no entry for <mark style="color:purple;">**`UPX`**</mark> Binaries in <mark style="color:blue;">**METADATA**</mark> & also no <mark style="color:red;">**CHECKSUMS**</mark>
- <mark style="color:purple;">**`UPX`**</mark> Binaries can still be decompressed <mark style="color:orange;">**`upx -d $BIN.upx`**</mark> & then checked for original <mark style="color:red;">**CHECKSUMS**</mark>
-   **Note**: If a build was completed recently, it's <mark style="color:purple;">**`UPX`**</mark> packed version may need some time to show up (Because it's done as post-build)

    > * Hence, raw binary may be a newer version while it's `UPX` may still be from the old one. In this case, using `UPX` to decompress & verify checksum will fail.
    > * `UPX` counterparts generally take **5-10** hrs to show up, packed fresh from the latest batch.


- **Note**: **ALL Binaries may NOT have&#x20;**<mark style="color:purple;">**`UPX`**</mark> Versions
- **Note**: AntiVirus Systems often detect<mark style="color:purple;">**`UPX`**</mark> as malicious, It is a known issue: [https://github.com/upx/upx/issues/437](https://github.com/upx/upx/issues/437)
{% endhint %}

***

### **Setup & Configure Local Build Environment**

* [x] Install [**Docker**](https://github.com/docker/docker-install) & [**Podman**](https://github.com/Azathothas/Toolpacks/tree/main/.github/runners#additional-notes--refs)
* [x] **Run** (_May Differ based on Your Host_)

> {% code overflow="wrap" %}
> ```bash
> !#Automatically picks up correct $ARCH & $IMAGE based on Host
> sudo podman run --detach --privileged --network="bridge" --publish "22222:22" --systemd="always" --ulimit="host" --volume="/tmp:/tmp" --tz="UTC" --pull="always" --name="toolpacker-dbg" "docker.io/azathothas/ubuntu-systemd-base:$(uname -m)"
>
> !#Add SSH Keys (Replace with yours)
> sudo podman exec -it -u "runner" "toolpacker-dbg" bash -c 'bash <(curl -qfsSL "https://pub.ajam.dev/repos/Azathothas/Arsenal/misc/Linux/install_dev_tools.sh")'
> sudo podman exec -it -u "runner" "toolpacker-dbg" bash -c 'sudo curl -qfsSL "https://github.com/Azathothas.keys" | sudo sort -u -o "/etc/ssh/authorized_keys" ; sudo systemctl restart sshd'
>
> !#SSH IN
> echo -e "\n[+] HOST_IP : $(ip -4 addr show $(ip route | grep default | awk '{print $5}') | grep -oP '(?<=inet\s)\d+(\.\d+){3}')\n"
> ssh "runner@$HOST_IP" -p "22222" -o "StrictHostKeyChecking=no" -i "$PATH_TO_SSH_KEY"
> #After SSH, the source script sets up ENV & PATH
> source <(curl -qfsSL "https://raw.githubusercontent.com/Azathothas/Toolpacks/main/.github/scripts/$(uname -m)_Linux/env.sh")
>
> !#STOP/DEL
> sudo podman stop "toolpacker-dbg"
> sudo podman rm "toolpacker-dbg" --force 2>/dev/null
> ```
> {% endcode %}

***

### **Why not host on GitHub?**

{% hint style="info" %}
[**@Azathothas**](https://docs.pkgforge.dev/orgs/pkgforge-core/people#azathothas) used to do just that back when there were only a few hundred binaries. All binaries were hosted on GitHub along with weekly releases containing all Binaries packed in tar/7z.

* You can find this on the [WayBack Archive](https://web.archive.org/web/*/https://github.com/Azathothas/Toolpacks): [https://web.archive.org/web/\*/https://github.com/Azathothas/Toolpacks](https://web.archive.org/web/*/https://github.com/Azathothas/Toolpacks)
* As number of packages grew, Git turned out to be not the right tool: [https://www.reddit.com/r/git/comments/ek4kv2/git\_is\_bad\_at\_binary\_file\_management\_but\_is\_it/](https://www.reddit.com/r/git/comments/ek4kv2/git_is_bad_at_binary_file_management_but_is_it/)
{% endhint %}

1. Because GitHub has very conservative limits: [https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github)
2. [**CloudFlare R2**](https://developers.cloudflare.com/r2/) is a [geo-distributed storage bucket](https://www.cloudflare.com/network/) & can scale up infinitely.&#x20;

{% hint style="info" %}
[**@Azathothas**](https://docs.pkgforge.dev/orgs/pkgforge-core/people#azathothas) did an [indepth comparision & analysis](https://ajam.dev/affordable-performant-s3-compatible-storage-providers) a while ago, you can read it here: [https://ajam.dev/affordable-performant-s3-compatible-storage-providers](https://ajam.dev/affordable-performant-s3-compatible-storage-providers)
{% endhint %}

3. Last but not least, to avoid [https://docs.pkgforge.dev/orgs/pkgforge-core/projects/pkgcache/dmca-or-copyright-cease-and-desist](https://docs.pkgforge.dev/orgs/pkgforge-core/projects/pkgcache/dmca-or-copyright-cease-and-desist)

### Android Deprecation

{% hint style="warning" %}
Android Support was deprecated on [**`Nov 18, 2024`**](https://github.com/Azathothas/Toolpacks/issues/38#issuecomment-2482936345)
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
Windows Support was deprecated on [**`Nov 18, 2024`**](https://github.com/Azathothas/Toolpacks/issues/38#issuecomment-2482936345)
{% endhint %}

1. Windows is **centralized** & thus benefits from central App Stores like the [**Windows Store**](https://apps.microsoft.com/home?hl=en-US\&gl=US) & [**WinGet**](https://learn.microsoft.com/en-us/windows/package-manager/winget/)
2. It has some of the same issues, Android has, i.e. can't be fully statically linked.
3. There already exist [<mark style="color:purple;">**UniGetUI**</mark>](https://github.com/marticliment/UniGetUI) , which is a pretty & mature wrapper around [WinGet](https://learn.microsoft.com/en-us/windows/package-manager/), [Scoop](https://scoop.sh/), [Chocolatey](https://chocolatey.org/), [Pip](https://pypi.org/), [Npm](https://www.npmjs.com/), [.NET Tool](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-tool-install), [PowerShell Gallery](https://www.powershellgallery.com/) and [**more**](https://github.com/marticliment/UniGetUI?tab=readme-ov-file#supported-package-managers)

### More Architectures & OS

* We would like to build binaries for other architectures like [**`riscv64`**](https://en.wikipedia.org/wiki/RISC-V), and the [BSD Family of OSes](https://en.wikipedia.org/wiki/Comparison_of_BSD_operating_systems), however our time & especially **RESOURCES** are limited.
* If you would like to see additional build targets prioritized, donating a <mark style="color:orange;">**Dedicated Build Server**</mark> would be the optimal encouragement.

{% hint style="warning" %}
- Note: <mark style="color:orange;">`32-Bit`</mark> Binaries will likely never be Supported/Added since that's now ancient and even embedded devices now ship with `64-Bit` **ARCH**
{% endhint %}

***

### bin.pkgforge.dev

{% hint style="info" %}
There's no public source code for the web frontend powering [https://bin.pkgforge.dev/](https://bin.pkgforge.dev/)
{% endhint %}

* [bin.pkgforge.dev](https://bin.pkgforge.dev/) is **NOT a web server**. It's a [web proxy](https://developers.cloudflare.com/r2/buckets/public-buckets/#connect-a-bucket-to-a-custom-domain) to an [R2 Bucket](https://developers.cloudflare.com/r2/buckets/public-buckets/)
* Internally, it uses a fork of [cmj2002/r2-dir-list](https://github.com/cmj2002/r2-dir-list) with [Hardcoded Cloudflare Credentials](https://developers.cloudflare.com/fundamentals/api/get-started/create-token/)
* The content can always be verified by comparing **CHECKSUMS**, published on GitHub (via Publicly Auditable & Log Viewable) Actions & on the Bucket. See [security.md](../../../../repositories/pkgforge-stable/security.md "mention")

***

### Public Tools Search

* [**GitHub Search**](https://github.com/search?q=is%3Apublic+archived%3Afalse+template%3Afalse+lang%3Ac+lang%3Acrystal+lang%3Ago+lang%3Anim+lang%3Arust+lang%3Azig+stars%3A%3E5+cli+OR+tool+OR+utility\&type=repositories\&s=updated\&o=desc): <mark style="color:orange;">`is:public archived:false template:false lang:c lang:crystal lang:go lang:nim lang:rust lang:zig stars:>5 cli OR tool OR utility`</mark> (**Sorted By**: <mark style="color:purple;">`Recently Updated`</mark>)
* [GitHub Issues](https://github.com/Azathothas/Toolpacks/blob/main/.github/pub_issues.txt): [https://github.com/Azathothas/Toolpacks/blob/main/.github/pub\_issues.txt](https://github.com/Azathothas/Toolpacks/blob/main/.github/pub_issues.txt)
* **List**: [https://github.com/stars/Azathothas/lists/toolpacks-tba](https://github.com/stars/Azathothas/lists/toolpacks-tba)

***

### Public Code Search

* [**GitHub Search**](https://github.com/search?q=NOT+user%3AAzathothas+NOT+user%3Axplshn+NOT+user%3Ametis-os+NOT+user%3Apkgforge+NOT+user%3Apkgforge-community+NOT+user%3Apkgforge-dev+NOT+user%3Apkgforge-security+NOT+is%3Afork+pkgforge.dev\&type=code): <mark style="color:orange;">`NOT user:Azathothas NOT user:xplshn NOT user:metis-os NOT user:pkgforge NOT user:pkgforge-community NOT user:pkgforge-dev NOT user:pkgforge-security NOT is:fork pkgforge.dev`</mark>
* [**Google**](https://www.google.com)**|**[**Bing**](https://www.bing.com/)**|**[**Baidu**](https://www.baidu.com): <mark style="color:orange;">`"*pkgforge.dev" -site:pkgforge.dev -site:ajam.dev`</mark>

***

### History & Lore

{% hint style="success" %}
* This, at the time of writing is, the [**largest collection**](https://github.com/Azathothas/Toolpacks#-status-) of [_`downloadable`_ (without requiring compilation)](https://bin.pkgforge.dev/) & [_`up-to-date`_](https://github.com/Azathothas/Toolpacks/commits/main/) [static binaries](https://en.wikipedia.org/wiki/Static_build) available on the public web.
* **`More >`** than all of these _COMBINED_: [andrew-d/static-binaries](https://github.com/andrew-d/static-binaries), [s.minos.io/archive/](https://github.com/minos-org/minos-static), [polaco1782/linux-static-binaries](https://github.com/polaco1782/linux-static-binaries), [borestad/static-binaries](https://github.com/borestad/static-binaries), [files.serverless.industries/bin/](https://github.com/perryflynn/static-binaries), [mosajjal/binary-tools](https://github.com/mosajjal/binary-tools), [ryanwoodsmall/static-binaries](https://github.com/ryanwoodsmall/static-binaries), [bol-van/bins](https://github.com/bol-van/bins)
* All of the projects listed above, served as inspirations at one point, so we thank the authors of these projects from the deepest of our hearts. PkgForge wouldn't exist without their work.
{% endhint %}

[**@Azathothas**](https://docs.pkgforge.dev/orgs/pkgforge-core/people#azathothas) used to be [bug bounty hunter](https://en.wikipedia.org/wiki/Bug_bounty_program), a long time ago in another life. He often had to set up pentesting environments on remote Servers, at that time there used to be [https://github.com/six2dez/reconftw](https://github.com/six2dez/reconftw), which installed a bunch of tools (often installing go/rust just to install the tools), this made the setup time awfully slow & frustrated him.

Eventually, <mark style="color:orange;">**`~ July, 2023`**</mark>, he would start modifying the setup scripts, as well as maintaining some homegrown scripts by himself. In the best of case, it was simply a wrapper around [eget](https://github.com/zyedidia/eget), to just fetch a precompiled binary from GitHub. In the worst of cases, it was installing go/rust toolchains, same as reconftw was doing just to install the tools. So he started creating repos on GitHub to build & release these binaries using GH's CI, and then using eget to pull them. The number of repos grew, and it was harder and harder to maintain each, thus [ToolPacks](https://github.com/Azathothas/Toolpacks/tree/main) was created to centralize them all. You can find all the several iterations this repository went through over the years, on the [web-archive](https://web.archive.org/web/20240000000000*/https://github.com/Azathothas/Toolpacks).

[**@Azathothas**](https://docs.pkgforge.dev/orgs/pkgforge-core/people#azathothas) recommends reading these articles if you need a technical justification:

* [x] ["Static Linking Considered Harmful" Considered Harmful](https://gavinhoward.com/2021/10/static-linking-considered-harmful-considered-harmful/)
* [x] [Dynamic Linking Is Bad For Apps And Static Linking Is Also Bad For Apps](https://belkadan.com/blog/2022/02/Dynamic-Linking-and-Static-Linking/)
* [x] [Oasis Linux](https://github.com/oasislinux/oasis) & [Anton Samokhvalov](https://github.com/pg83)'s [Stalix](https://stal-ix.github.io/STALIX.html) both are distros specifically using only Static Binaries. Check their project page to learn Why.
* [x] And then we have things like [Cosmopolitan Libc](https://github.com/jart/cosmopolitan) & [T2 SDE](https://t2sde.org/about.html), they are very different from a Static Binary POV, but their rationale for doing so applies to why Static Binaries must exist.

A special mention to [**@pwnwriter**](https://github.com/pwnwriter) who reached out to [**@Azathothas**](https://docs.pkgforge.dev/orgs/pkgforge-core/people#azathothas), and created the very first Package manager [**Hysp**](https://github.com/pwnwriter/hysp) **\~** [`Nov 17, 2023`](https://github.com/pwnwriter/hysp/commits/main/?after=f9f9f3c3933b6ed35f0682bdec91d420430f898e+104) . Sadly,  [**Hysp**](https://github.com/pwnwriter/hysp) was **archived on May 26, 2024**.&#x20;

Another mention to [**@Xplshn**](https://github.com/xplshn) who created a package manager in sh called [**bdl**](https://github.com/xplshn/Handyscripts/blob/master/bdl) [`~ Dec 20, 2023`](https://github.com/xplshn/Handyscripts/commits/master/bdl?after=3505b7757e01d41ea45bc24203a68a0ec0aa9c64+34), which later turned into the Golang [**BigDL**](https://github.com/xplshn/bigdl) [`~ Feb 5, 2024`](https://github.com/xplshn/bigdl/commits/master/?after=f54b3ea0d1465993b97acb8b332c226d307223f6+349), which again turned int**o** [**Dbin**](https://github.com/xplshn/dbin) [`~ Aug 23, 2024`](https://github.com/xplshn/dbin/commit/5ae3f34eb2c3995919c06e14f92750f9802068af).

Seeing all these efforts, and some encouragements on [Lobsters](https://lobste.rs/s/iqxjee/poor_man_s_package_manager_only),  [**@Azathothas**](https://docs.pkgforge.dev/orgs/pkgforge-core/people#azathothas) approached [**@QaidVoid**](https://github.com/QaidVoid) and [**Soar**](https://github.com/pkgforge/soar) received it's first commit on [**`Oct 3, 2024`**](https://github.com/pkgforge/soar/commit/06331f438a35dbb40da868fdc606b71f0272d7d9). One thing led to another, and the [**PkgForge**](https://github.com/pkgforge) Organization came into being on **`Nov 4, 2024`** to do everything _**officially**_ and have more control over the direction of all our projects.
