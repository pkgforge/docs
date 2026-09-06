---
icon: box
description: Portable AppImages
---

# Anylinux-AppImages

[Anylinux-AppImages](https://github.com/pkgforge-dev/Anylinux-AppImages) builds AppImages designed to run on any Linux distribution, including very old ones and musl-based ones. They bundle everything they need instead of depending on host libraries, which is what most other AppImages get wrong.

Most are made with [sharun](https://github.com/pkgforge-dev/Anylinux-sharun) and ship the [uruntime](https://github.com/VHSgunzo/uruntime) rather than the standard AppImage runtime.

## What that buys you

* **No host requirements worth the name.** The runtime mounts with FUSE where `fusermount` exists, falls back to [user namespaces](../../../formats/packages/errors-and-quirks/namespaces.md) where it does not, and falls back again to extracting into `TMPDIR` and running from there.
* **No dependency on the host libc.** Works on glibc and musl systems alike, and on distributions far older than the build machine.
* **No FHS layout required.** They run directly on NixOS, with no wrapper. Do not put them through `appimage-run`, which [breaks them](../../../formats/packages/appimage/).
* **Smaller than the alternatives**, thanks to [DwarFS](https://github.com/mhx/dwarfs) and [debloated packages](https://github.com/pkgforge-dev/archlinux-pkgs-debloated).

## Further reading

* [FAQ](https://github.com/pkgforge-dev/Anylinux-AppImages/blob/main/FAQ.md)
* [How to make these](https://github.com/pkgforge-dev/Anylinux-AppImages/blob/main/HOW-TO-MAKE-THESE.md)
* [Size comparison against Flatpak](https://github.com/pkgforge-dev/Anylinux-AppImages/blob/main/disk-usage-vs-flatpak.md)
