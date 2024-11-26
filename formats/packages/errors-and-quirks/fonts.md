---
icon: font-case
description: Issues related to fonts
---

# Fonts

{% hint style="info" %}
In attempt to **minimize size** & cater to all Locales/Fonts, [..](../ "mention") **aren't shipped with Fonts/Icons.**

Instead, **they use the fonts from the Host**.
{% endhint %}

***

### [Alpine](https://wiki.alpinelinux.org/wiki/Fonts)

{% code title="Installing Fonts on AlpineLinux" overflow="wrap" %}
```shell
!#Use doas/sudo wherever applicable
apk update --no-interactive
packages="fontconfig font-awesome font-inconsolata font-noto font-terminus font-unifont"
for pkg in $packages; do apk add "$pkg" --latest --upgrade --no-interactive ; done
fc-cache --force --verbose || sudo fc-cache --force --verbose
#Ideally logout/login again or Restart your system
```
{% endcode %}

***

### [Arch](https://wiki.archlinux.org/title/Fonts) & [Derivatives](https://wiki.archlinux.org/title/Arch-based_distributions)

{% code title="Installing Fonts on ArchLinux" overflow="wrap" %}
```sh
!#Use doas/sudo wherever applicable
pacman -y --sync --refresh --noconfirm
packages="fontconfig noto-fonts otf-font-awesome terminus-font ttf-dejavu ttf-inconsolata-nerd"
for pkg in $packages; do pacman -Sy "$pkg" --noconfirm ; done
fc-cache --force --verbose || sudo fc-cache --force --verbose
#Ideally logout/login again or Restart your system
```
{% endcode %}

***

### [Debian](https://wiki.debian.org/Fonts) & [Derivatives](https://en.wikipedia.org/wiki/Category:Debian-based_distributions)

{% code title="Installing Fonts on Debian" %}
```sh
!#Use doas/sudo wherever applicable
sudo apt update -y -qq && sudo apt install fontconfig fonts-noto -y
fc-cache --force --verbose || sudo fc-cache --force --verbose
#Ideally logout/login again or Restart your system
```
{% endcode %}
