---
icon: list-check
description: Worked recipes
---

# Examples

Every recipe here is a real one from [soarpkgs](https://github.com/pkgforge/soarpkgs/tree/main/packages), trimmed only where a long list would get in the way. Start from whichever is closest to the package you are adding.

## A static binary from an upstream release

The common case. Upstream publishes a musl tarball per architecture, the recipe globs it, and `[source.install]` takes out the binary along with the manual page, the completions and the licences.

```toml
[pkg]
name        = "ripgrep"
type        = "static"
description = "A search tool that combines the usability of ag with the raw speed of grep"
homepage    = ["https://github.com/BurntSushi/ripgrep"]
license     = ["MIT", "Unlicense"]
maintainer  = ["QaidVoid (contact@qaidvoid.dev)"]
category    = ["ConsoleOnly", "Utility"]
repology    = ["ripgrep"]

[host]
supported = ["x86_64-linux", "aarch64-linux"]

[update]
strategy = "github-releases"
repo     = "BurntSushi/ripgrep"

[source]
github = "BurntSushi/ripgrep"
glob   = "ripgrep-${version}-${arch}-unknown-linux-musl.tar.gz"

[source.install]
"*/COPYING"          = "COPYING"
"*/LICENSE-MIT"      = "LICENSE-MIT"
"*/UNLICENSE"        = "UNLICENSE"
"*/rg"               = "bin/rg"
"*/complete/rg.bash" = "share/bash-completion/completions/rg"
"*/complete/rg.fish" = "share/fish/vendor_completions.d/rg.fish"
"*/doc/rg.1"         = "share/man/man1/rg.1"
"*/complete/_rg"     = "share/zsh/site-functions/_rg"
```

Note the glob in the install paths. `*/` matches whatever the tarball's top directory is called, which saves repeating the version in every line.

## An upstream that names architectures its own way

`[arch]` maps our host names onto upstream's, and `${arch}` picks up the mapped value. The licence is not in the archive, so `[[extra]]` fetches it. It is served from a branch, so it is pinned by URL but not by hash.

```toml
[pkg]
name        = "fzf"
type        = "static"
description = "A command-line fuzzy finder"
homepage    = ["https://github.com/junegunn/fzf"]
license     = ["MIT"]
category    = ["ConsoleOnly", "Utility"]
repology    = ["fzf"]

[host]
supported = ["aarch64-linux", "x86_64-linux", "riscv64-linux"]

[arch]
aarch64 = "arm64"
x86_64  = "amd64"
riscv64 = "riscv64"

[update]
strategy     = "github-releases"
repo         = "junegunn/fzf"
strip-prefix = "v"

[source]
github = "junegunn/fzf"
glob   = "*linux_${arch}.tar.gz"

[source.install]
"fzf" = "bin/fzf"

[[extra]]
url    = "https://raw.githubusercontent.com/junegunn/fzf/master/LICENSE"
to     = "LICENSE"
verify = false
```

## An upstream whose filenames do not follow a pattern

`fnm` publishes `fnm-linux.zip` and `fnm-arm64.zip`. No template and no `[arch]` mapping produces both, so each host names its own URL.

```toml
[source]

[source.url]
x86_64-linux  = "https://github.com/Schniz/fnm/releases/download/v${version}/fnm-linux.zip"
aarch64-linux = "https://github.com/Schniz/fnm/releases/download/v${version}/fnm-arm64.zip"

[source.install]
"fnm" = "bin/fnm"
```

## An AppImage

The artifact is the package, so there is nothing to install out of it. When the AppImage should land under a different command name, or carry aliases, the long form says so without naming a source path.

```toml
[pkg]
name        = "dunst"
type        = "appimage"
description = "Lightweight and customizable notification daemon"
homepage    = [
  "https://dunst-project.org",
  "https://github.com/pkgforge-dev/dunst-AppImage",
]
license    = ["BSD-3-Clause"]
maintainer = ["Samueru-sama (github.com/Samueru-sama)"]
category   = ["System", "Utility"]
repology   = ["dunst"]

[host]
supported = ["x86_64-linux", "aarch64-linux"]

[update]
strategy   = "github-releases"
repo       = "pkgforge-dev/dunst-AppImage"
tag-suffix = "strip"

[source]
github = "pkgforge-dev/dunst-AppImage"
glob   = "*${arch}*.appimage"

[[source.install]]
to         = "bin/dunst"
symlink_as = ["dunstctl", "dunstify"]
```

## A package one host gets from us

Upstream serves x86_64 and aarch64, but not riscv64, so that host is served from [pkgforge/builds](builds.md). Three things follow. `[update]` tracks our repository rather than upstream, so the version pinned is one every host can download. `[pkg] src` keeps naming the real upstream. And riscv64 names its own install list, because our archive does not unpack the way upstream's does.

```toml
[pkg]
name        = "nushell"
type        = "static"
description = "A new type of shell"
src         = ["https://github.com/nushell/nushell"]
homepage    = ["https://www.nushell.sh"]
license     = ["MIT"]

[host]
supported = ["x86_64-linux", "aarch64-linux", "riscv64-linux"]

[update]
strategy   = "github-releases"
repo       = "pkgforge/builds"
tag-prefix = "nushell-"

[source]

[source.url]
x86_64-linux  = "https://github.com/nushell/nushell/releases/download/${version}/nu-${version}-${arch}-unknown-linux-musl.tar.gz"
aarch64-linux = "https://github.com/nushell/nushell/releases/download/${version}/nu-${version}-${arch}-unknown-linux-musl.tar.gz"
riscv64-linux = "https://github.com/pkgforge/builds/releases/download/nushell-${version}/nushell-${version}-riscv64-linux.tar.gz"

[source.install]
"nu-${version}-${arch}-unknown-linux-musl/LICENSE" = "LICENSE"
"nu-${version}-${arch}-unknown-linux-musl/nu"      = "bin/nu"

[source.install.riscv64-linux]
"nu"      = "bin/nu"
"LICENSE" = "LICENSE"
```

Naming riscv64 replaces the shared list for that host alone. The other two keep it.

## The version file this produces

Written by `sbuild resolve` and `sbuild hashfill`, not by hand.

```toml
version = "0.11.5"
date    = "2026-07-28T10:51:15Z"

[url]
x86_64-linux = "https://github.com/pkgforge/builds/releases/download/amdgpu_top-0.11.5/amdgpu_top-0.11.5-x86_64-linux.tar.gz"

[blake3]
x86_64-linux = "0be0c51861271fe75f5d5e8e7b28d6658497ade369b41b02ae525b27a5e76d87"

[sha256]
x86_64-linux = "b09045fca42665bdb944d85bbb30627939f992b56d5df3e45a1ba17e54a38901"

[size]
x86_64-linux = 9746766
```
