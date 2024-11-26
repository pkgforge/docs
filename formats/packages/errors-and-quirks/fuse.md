---
description: Setting up Fuse
icon: eject
---

# Fuse

{% hint style="info" %}
* [AppImage](https://github.com/AppImage/AppImageSpec/blob/master/draft.md) has official Guide: [https://github.com/appimage/appimagekit/wiki/fuse](https://github.com/appimage/appimagekit/wiki/fuse)
* `Note`: If you have **`fuse(2)`**, consider upgrading to **`fuse3`**, some distros may require either **`fuse(2)`** OR **`fuse(3)`** NOT both, **choose `fuse3`**
* Your distro should already come with the [kernel modules](https://docs.kernel.org/filesystems/fuse.html), and generally, only the [libraries](https://github.com/libfuse/libfuse)/[programs](https://man7.org/linux/man-pages/man1/fusermount3.1.html) need to be installed:
{% endhint %}

***

### [Alpine](https://wiki.alpinelinux.org/wiki/Installation#Daily_driver_guide)

{% code overflow="wrap" %}
```bash
!#Use doas/sudo wherever applicable
apk update --no-interactive
apk add fuse fuse3 --latest --upgrade --no-interactive
```
{% endcode %}

***

### [ArchLinux](https://wiki.archlinux.org/title/FUSE) & [Derivatives](https://wiki.archlinux.org/title/Arch-based_distributions)

{% code overflow="wrap" %}
```bash
!#Use doas/sudo wherever applicable
pacman -y --sync --refresh --noconfirm
#Ideally, having both fuse2 & fuse3 side by side works, if it doesn't only install fuse3
pacman -Sy fuse2 fuse3 --noconfirm
```
{% endcode %}

***

### [Debian](https://packages.debian.org/search?keywords=fuse3) & [Derivatives](https://en.wikipedia.org/wiki/Category:Debian-based_distributions)

{% code overflow="wrap" %}
```bash
!#Use doas/sudo wherever applicable
sudo apt update -y -qq
sudo apt install fuse3 -y
```
{% endcode %}

***

{% hint style="info" %}
* **Fusermount**: [https://command-not-found.com/fusermount](https://command-not-found.com/fusermount)
* **Fusermount3**: [https://command-not-found.com/fusermount3](https://command-not-found.com/fusermount3)
{% endhint %}

