---
icon: clipboard-list
description: SBUILD Examples
---

# Examples

## Minimal

{% code overflow="wrap" %}
```yaml
#!/SBUILD ver @v1.0.0
pkg: "86box"
pkgver: "v4.2.1"
description: "Emulator of x86-based machines"
src_url:
  - "https://github.com/86Box/86Box"
x_exec:
  shell: "bash"
  pkgver: |
    curl -qfsSL "https://api.github.com/repos/86Box/86Box/releases/latest" | jq -r '.tag_name'
  run: |
    case "$(uname -m)" in
      aarch64)
        soar dl "https://github.com/86Box/86Box" --match "appimage,arm64" --exclude "x64,x86,zsync" -o "./${PKG}" --yes
        ;;
      x86_64)
        soar dl "https://github.com/86Box/86Box" --match "appimage,x86_64" --exclude "aarch64,arm,zsync" -o "./${PKG}" --yes
        ;;
    esac
```
{% endcode %}

## Full Example

{% code overflow="wrap" %}
```yaml
#!/SBUILD ver @v1.0.0

pkg: "86box"
pkg_id: "github.com.86Box.86Box"
pkg_type: "AppImage"
pkgver: "v4.2.1" #fixed version; omit for dynamic versioning
#ghcr_pkg: "86box" #optional: set fixed ghcr path

app_id: "net._86box._86Box"
build_util:
  - "curl#bin"
  - "jq#bin"
category:
  - "Emulator"
description: "Emulator of x86-based machines"
homepage:
  - "https://86box.net"
license:
  - id: "GPL-2.0"
    url: "https://github.com/86Box/86Box/raw/main/COPYING"
maintainer:
  - "Azathothas (https://github.com/Azathothas)"
note:
  - "You need to download ROMS: https://86box.readthedocs.io/en/latest/usage/roms.html"
provides:
  - "86box"
repology:
  - "86box"
src_url:
  - "https://github.com/86Box/86Box"
tag:
  - "emulator"
x_exec:
  host:
    - "aarch64-Linux"
    - "x86_64-Linux"
  shell: "bash"
  pkgver: |
    curl -qfsSL "https://api.github.com/repos/86Box/86Box/releases/latest" | jq -r '.tag_name'
  run: |
    case "$(uname -m)" in
      aarch64)
        soar dl "https://github.com/86Box/86Box" --match "appimage,arm64" --exclude "x64,x86,zsync" -o "./${PKG}" --yes
        ;;
      x86_64)
        soar dl "https://github.com/86Box/86Box" --match "appimage,x86_64" --exclude "aarch64,arm,zsync" -o "./${PKG}" --yes
        ;;
    esac
```
{% endcode %}

## Rolling Build

For packages without versioned releases (nightly, git HEAD):

{% code overflow="wrap" %}
```yaml
#!/SBUILD ver @v1.0.0

pkg: "example-nightly"
_rolling: true
description: "Nightly build example"
src_url:
  - "https://github.com/example/repo"
x_exec:
  shell: "bash"
  pkgver: |
    echo "nightly-$(date +%Y%m%d)"
  run: |
    # build from git HEAD
```
{% endcode %}
