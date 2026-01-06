---
icon: hard-drive
description: Required for mounting Filesystems & Images
---

# FUSE

{% hint style="info" %}
Required for mounting Filesystems & Images

Can still be run with `--appimage-extract-and-run` | `APPIMAGE_EXTRACT_AND_RUN=1`
{% endhint %}

AppImages and similar formats use FUSE (Filesystem in Userspace) to mount themselves.

## Common Errors

```
fusermount: mount failed: Operation not permitted
```

```
Cannot mount AppImage, please check your FUSE setup
```

## Solutions

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

### Extract Instead

Most AppImages support extraction as fallback:

```bash
./app.AppImage --appimage-extract-and-run
```

Or set the environment variable:
```bash
APPIMAGE_EXTRACT_AND_RUN=1 ./app.AppImage
```

Manual extraction:
```bash
./app.AppImage --appimage-extract
./squashfs-root/AppRun
```

### Use Type-3 AppImages

Type-3 AppImages don't require FUSE - they use `squashfuse` embedded in the runtime.
