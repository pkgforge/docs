---
description: Frequently Asked Questions & Misc
icon: message-question
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

