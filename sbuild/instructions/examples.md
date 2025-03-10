---
icon: clipboard-list
description: A Few Examples
---

# Examples

## Minimal

<pre class="language-yaml" data-overflow="wrap"><code class="lang-yaml">#!/SBUILD ver @v1.0.0
_disabled: false
pkg: "86box"
build_util:
  - "curl#bin"
  - "jq#bin"
description: "Emulator of x86-based machines"
src_url:
 - "https://github.com/86Box/86Box"
x_exec:
  shell: "bash"
  pkgver: |
    #This will fetch the version and save it as <a data-footnote-ref href="#user-content-fn-1">"./${PKG}.version" and env ${PKG_VER}</a>
    curl -qfsSL "https://api.github.com/repos/86Box/86Box/releases/latest" | jq -r '.tag_name'
  run: |
    #Remember we are inside some random dir and we have got the env vars injected ($PKG etc)
    ##Download the file
    case "$(uname -m)" in
      aarch64)
        soar dl "https://github.com/86Box/86Box" --match "appimage,arm64" --exclude "x64,x86,zsync" -o "./${PKG}" --yes &#x26;&#x26; chmod +x "./${PKG}"
        ;;
      x86_64)
        soar dl "https://github.com/86Box/86Box" --match "appimage,x86_64" --exclude "aarch64,arm,zsync" -o "./${PKG}" --yes &#x26;&#x26; chmod +x "./${PKG}"
        ;;
    esac
    #We are done and can let the Runner take it from here
</code></pre>

### Generic (Recommended)

{% code overflow="wrap" %}
```yaml
#!/SBUILD ver @v1.0.0
_disabled: false

pkg: "86box"
pkg_id: "github.com.86Box.86Box"
pkg_type: "AppImage"
app_id: "net._86box._86Box"
build_util:
  - "curl#bin"
  - "jq#bin"
category:
  - "Emulator"
description: "Emulator of x86-based machines"
distro_pkg:
  archlinux:
    aur:
      - "86box"
      - "86box-appimage"
      - "86box-git"
  nixpkgs:
    - "86Box"
homepage:
  - "https://86box.net"
  - "https://86box.readthedocs.io"
license:
  - id: "GPL-2.0" #spdx identifier
    url: "https://github.com/86Box/86Box/raw/ae5b6909a2a8d3b2098d5467a86fefcf81c20e30/COPYING" #RAW Permalink to License
maintainer:
  - "Azathothas (https://github.com/Azathothas)"
note:
 - "Officially Created AppImage. Check/Report @ https://github.com/86Box/86Box"
 - "You need to download ROMS: https://86box.readthedocs.io/en/latest/usage/roms.html"
provides:
  - "86box" #explictly states what progs are available upon build completion
repology:
  - "86box"
src_url:
  - "https://github.com/86Box/86Box"
tag:
  - "app-emulation"
  - "emulators"
  - "game"
  - "system"
x_exec:
  host:
    - "aarch64-Linux" #Explictly states it supports aarch64 Linux
    - "x86_64-Linux" #Explictly states it supports x86_64 Linux
  shell: "bash"
  pkgver: |
    #This will fetch the version and save it as "./${PKG}.version" and env ${PKG_VER}
    curl -qfsSL "https://api.github.com/repos/86Box/86Box/releases/latest" | jq -r '.tag_name'
  run: |
    #Remember we are inside some random dir and we have got the env vars injected (PKG etc)
    ##Download the file
    case "$(uname -m)" in
      aarch64)
        soar dl "https://github.com/86Box/86Box" --match "appimage,arm64" --exclude "x64,x86,zsync" -o "./${PKG}" --yes && chmod +x "./${PKG}"
        ;;
      x86_64)
        soar dl "https://github.com/86Box/86Box" --match "appimage,x86_64" --exclude "aarch64,arm,zsync" -o "./${PKG}" --yes && chmod +x "./${PKG}"
        ;;
    esac
    #We are done and can let the Runner take it from here
```
{% endcode %}





[^1]: Yes, we don't have to write to any files ourselves, the SBUILDER (Linter/Runner) will do it for us
