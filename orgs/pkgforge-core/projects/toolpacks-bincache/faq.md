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
2. &#x20;[aarch64-Linux](https://github.com/Azathothas/Toolpacks/blob/main/aarch64_arm64_Linux/BUILD_ERROR.log.md) : [https://github.com/Azathothas/Toolpacks/blob/main/aarch64\_arm64\_Linux/BUILD\_ERROR.log.md](https://github.com/Azathothas/Toolpacks/blob/main/aarch64_arm64_Linux/BUILD_ERROR.log.md)
3. &#x20;[x86\_64-Linux](https://github.com/Azathothas/Toolpacks/blob/main/x86_64_Linux/BUILD_ERROR.log.md) : [https://github.com/Azathothas/Toolpacks/blob/main/x86\_64\_Linux/BUILD\_ERROR.log.md](https://github.com/Azathothas/Toolpacks/blob/main/x86_64_Linux/BUILD_ERROR.log.md)
4. So if it's already there, it will eventually be fixed.
{% endhint %}

* [x] If it's NOT Or you would like us to fix it ASAP, [please create an Issue](https://github.com/Azathothas/Toolpacks/issues/new)

{% hint style="info" %}
- **Title**: Summary of Issue along with <mark style="color:orange;">**`Binary`**</mark> & <mark style="color:blue;">**`Platfrom`**</mark> Name
- **`Description`**: Show the <mark style="color:red;">**`crash/segfault`**</mark> screenshot or provide <mark style="color:orange;">**`file/ldd/readelf`**</mark> output along with what would be the correct behaviour
- **Tag**: <mark style="color:orange;">**`BUG`**</mark> + <mark style="color:blue;">**`$PLATFORM`**</mark>
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

1. Because GitHub has very conservative limits: [https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github)
2. [Hugging Face](https://huggingface.co/pricing) has [generous limits](https://huggingface.co/docs/hub/en/repositories-recommendations) & [inbuilt support for LFS](https://huggingface.co/docs/hub/en/repositories-getting-started)
3. Last but not least, to avoid [https://docs.pkgforge.dev/orgs/pkgforge-core/projects/pkgcache/dmca-or-copyright-cease-and-desist](https://docs.pkgforge.dev/orgs/pkgforge-core/projects/pkgcache/dmca-or-copyright-cease-and-desist)

***

### History & Lore

{% hint style="success" %}
* This, at the time of writing is, the [**largest collection**](https://github.com/Azathothas/Toolpacks#-status-) of [_`downloadable`_ (without requiring compilation)](https://bin.pkgforge.dev/) & [_`up-to-date`_](https://github.com/Azathothas/Toolpacks/commits/main/) [static binaries](https://en.wikipedia.org/wiki/Static_build) available on the public web.
* **`More >`** than all of these _COMBINED_: [andrew-d/static-binaries](https://github.com/andrew-d/static-binaries), [s.minos.io/archive/](https://github.com/minos-org/minos-static), [polaco1782/linux-static-binaries](https://github.com/polaco1782/linux-static-binaries), [borestad/static-binaries](https://github.com/borestad/static-binaries), [files.serverless.industries/bin/](https://github.com/perryflynn/static-binaries), [mosajjal/binary-tools](https://github.com/mosajjal/binary-tools), [ryanwoodsmall/static-binaries](https://github.com/ryanwoodsmall/static-binaries), [bol-van/bins](https://github.com/bol-van/bins)
* All of the projects listed above, served as inspirations at one point, so we thank the authors of these projects from the deepest of our hearts. PkgForge wouldn't exist without their work.
{% endhint %}

[**@Azathothas**](https://docs.pkgforge.dev/orgs/pkgforge-core/people#azathothas) used to be [bug bounty hunter](https://en.wikipedia.org/wiki/Bug_bounty_program), a long time ago in another life. He often had to set up pentesting environments on remote Servers, at that time there used to be [https://github.com/six2dez/reconftw](https://github.com/six2dez/reconftw), which installed a bunch of tools (often installing go/rust just to install the tools), this made the setup time awfully slow & frustrated him.

Eventually, he would start modifying the setup scripts, as well as maintaining some homegrown scripts by himself. In the best of case, it was simply a wrapper around [eget](https://github.com/zyedidia/eget), to just fetch a precompiled binary from GitHub. In the worst of cases, it was installing go/rust toolchains, same as reconftw was doing just to install the tools. So he started creating repos on GitHub to build & release these binaries using GH's CI, and then using eget to pull them. The number of repos grew, and it was harder and harder to maintain each, thus [ToolPacks](https://github.com/Azathothas/Toolpacks/tree/main) was created to centralize them all. You can find all the several iterations this repository went through over the years, on the [web-archive](https://web.archive.org/web/20240000000000*/https://github.com/Azathothas/Toolpacks).

[**@Azathothas**](https://docs.pkgforge.dev/orgs/pkgforge-core/people#azathothas) recommends reading these articles if you need a technical justification:

* [x] ["Static Linking Considered Harmful" Considered Harmful](https://gavinhoward.com/2021/10/static-linking-considered-harmful-considered-harmful/)
* [x] [Dynamic Linking Is Bad For Apps And Static Linking Is Also Bad For Apps](https://belkadan.com/blog/2022/02/Dynamic-Linking-and-Static-Linking/)
* [x] [Oasis Linux](https://github.com/oasislinux/oasis) & [Anton Samokhvalov](https://github.com/pg83)'s [Stalix](https://stal-ix.github.io/STALIX.html) both are distros specifically using only Static Binaries. Check their project page to learn Why.
* [x] And then we have things like [Cosmopolitan Libc](https://github.com/jart/cosmopolitan) & [T2 SDE](https://t2sde.org/about.html), they are very different from a Static Binary POV, but their rationale for doing so applies to why Static Binaries must exist.
