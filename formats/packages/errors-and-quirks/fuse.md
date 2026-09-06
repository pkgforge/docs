---
icon: hard-drive
description: Required by some formats for mounting the image
---

# FUSE

Most self-contained formats mount their own payload rather than unpacking it, and FUSE is what lets a normal user mount something. Whether you need anything installed for that depends on the runtime the package was built with.

{% hint style="success" %}
[**Anylinux AppImages**](../../../orgs/pkgforge-dev/projects/anylinux-appimages.md) need nothing. Their [uruntime](https://github.com/VHSgunzo/uruntime) embeds its own `squashfuse` and `dwarfs`, so it only calls `fusermount`. Where that is missing it retries under [user namespaces](namespaces.md), and where those are unavailable too it extracts into `TMPDIR`, runs, and cleans up after itself.

There is no `libfuse2` to install for these, and installing one changes nothing.
{% endhint %}

Traditional AppImages, built with `linuxdeploy` or similar, are the ones that need FUSE on the host, usually the older `libfuse2` that many distributions no longer install by default.

## Common errors

```
fusermount: mount failed: Operation not permitted
```

```
Cannot mount AppImage, please check your FUSE setup
```

```
dlopen(): error loading libfuse.so.2
```

## Solutions

### Extract instead

The fix that needs nothing installed. Most AppImages support it:

```bash
./app.AppImage --appimage-extract-and-run
```

```bash
APPIMAGE_EXTRACT_AND_RUN=1 ./app.AppImage
```

Or unpack it once and run what comes out:

```bash
./app.AppImage --appimage-extract
./squashfs-root/AppRun
```

### Install FUSE

**Debian/Ubuntu:**
```bash
sudo apt install fuse libfuse2
```

**Fedora:**
```bash
sudo dnf install fuse fuse-libs
```

**Arch:**
```bash
sudo pacman -S fuse2
```

### Use a package that does not need it

A static runtime that carries its own mounting code and falls back on its own is the real fix. That is what [Anylinux AppImages](../../../orgs/pkgforge-dev/projects/anylinux-appimages.md) do, and it is why the packages in [soarpkgs](../../../repositories/soarpkgs/) rarely run into any of this.
