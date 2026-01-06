---
icon: font
description: Font Issues
---

# Fonts

Portable packages may have font rendering issues due to missing fonts or fontconfig.

## Common Issues

- Missing fonts (squares or boxes instead of characters)
- Wrong font fallbacks
- CJK characters not rendering

## Solutions

### Install Common Fonts

**Debian/Ubuntu:**
```bash
sudo apt install fonts-noto fonts-liberation
```

**Fedora:**
```bash
sudo dnf install google-noto-fonts-common liberation-fonts
```

**Arch:**
```bash
sudo pacman -S noto-fonts ttf-liberation
```

### Set Font Environment

```bash
export FONTCONFIG_PATH=/etc/fonts
```
