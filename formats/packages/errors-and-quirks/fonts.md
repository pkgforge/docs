---
icon: font
description: Required to display/render Non-English Chars, Emojis, Symbols etc.
---

# Fonts

{% hint style="info" %}
Required to display/render Non-English Chars, Emojis, Symbols etc.
{% endhint %}

Portable packages may have font rendering issues due to missing fonts or fontconfig.

## Common Issues

- Missing fonts (squares or boxes instead of characters)
- Wrong font fallbacks
- CJK characters not rendering
- Emojis showing as boxes

## Solutions

### Install Common Fonts

**Debian/Ubuntu:**
```bash
sudo apt install fonts-noto fonts-liberation fonts-noto-color-emoji
```

**Fedora:**
```bash
sudo dnf install google-noto-fonts-common liberation-fonts google-noto-emoji-fonts
```

**Arch:**
```bash
sudo pacman -S noto-fonts noto-fonts-emoji ttf-liberation
```

### Set Font Environment

```bash
export FONTCONFIG_PATH=/etc/fonts
```
