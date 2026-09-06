---
icon: file-lines
description: pkg.toml reference
---

# Recipe

`pkg.toml` is the part of a package that survives a version bump: who the package is, which hosts it serves, how to find out that a new release exists, and how to find the artifact inside it. It is a template. The literal values live in the [version file](version-file.md).

```toml
[pkg]
name        = "gh"
type        = "static"
description = "GitHub CLI tool"
homepage    = ["https://cli.github.com"]
license     = ["MIT"]
maintainer  = ["Someone (you@example.com)"]
category    = ["ConsoleOnly", "Development"]
repology    = ["github-cli"]
provides    = ["gh"]

[host]
supported = ["x86_64-linux", "aarch64-linux", "riscv64-linux"]

[arch]
x86_64  = "amd64"
aarch64 = "arm64"
riscv64 = "riscv64"

[update]
strategy     = "github-releases"
repo         = "cli/cli"
strip-prefix = "v"

[source]
url = "https://github.com/cli/cli/releases/download/v${version}/gh_${version}_linux_${arch}.tar.gz"

[source.install]
"gh_${version}_linux_${arch}/bin/gh"  = "bin/gh"
"gh_${version}_linux_${arch}/LICENSE" = "LICENSE"
```

`name`, `description`, `[host]`, `[update]` and `[source]` are required. The upstream repository is taken from `[update] repo` and the package identifier from `name`, so neither is repeated.

***

## `[pkg]`

| Field | Type | Notes |
|---|---|---|
| `name` | string | Required. The name a user installs. |
| `type` | string | The [format](../formats/packages/) of the artifact, such as `static`, `appimage` or `onelf`. |
| `description` | string | Required. One line, no trailing period. |
| `homepage` | array | Project page. |
| `license` | array | SPDX identifiers. |
| `maintainer` | array | `Name (contact)`. |
| `category` | array | [FreeDesktop categories](https://specifications.freedesktop.org/menu-spec/latest/apa.html). |
| `repology` | array | Names this package is known by on [Repology](https://repology.org/). |
| `provides` | array | Commands the package makes available. |

The rest are for exceptions, and are better left out than stated to repeat a default:

| Field | Default | State it when |
|---|---|---|
| `family` | `name` | the directory name differs from the name the package installs under |
| `channel` | `stable` | the package tracks `unstable` or `nightly` |
| `src` | derived from `[update]` | upstream is not the repository the version comes from |
| `note` | none | there is something a user genuinely needs told, and no structured field says it |
| `portable` | `true` | the package needs something from the host, together with `portable-reason` |
| `disabled` | `false` | the package should not be installable, together with `disabled-reason` |

***

## `[host]` and `[arch]`

`[host] supported` lists what the package is published for. The hosts in use are `x86_64-linux`, `aarch64-linux` and `riscv64-linux`. Nothing is generated for a host that is not listed.

`[arch]` maps a host architecture onto whatever upstream calls it, and is only needed when the two differ:

```toml
[arch]
x86_64  = "amd64"
aarch64 = "arm64"
```

`${arch}` in a URL or an install path passes through this table first.

***

## `[update]`

`[update]` answers one question: which version is current. It is read by `sbuild resolve` and never by a client, because resolution has already happened by the time an index is built.

```toml
[update]
strategy     = "github-releases"
repo         = "BurntSushi/ripgrep"
strip-prefix = "v"
```

| Field | Notes |
|---|---|
| `strategy` | `github-releases`, `github-tags`, `gitlab-tags` or `html-regex`. |
| `repo` | The repository, or the page to scrape for `html-regex`. |
| `strip-prefix` | Removed from the tag to get the version, usually `v`. |
| `tag-prefix` | Only consider tags starting with this. Needed when one repository publishes releases for several packages. |
| `tag-suffix` | The same, at the other end. |
| `pattern` | Regular expression for `html-regex`. |

A package whose artifact for some host comes from [pkgforge/builds](builds.md) tracks that repository rather than upstream, and names its real origin in `[pkg] src`:

```toml
[update]
strategy   = "github-releases"
repo       = "pkgforge/builds"
tag-prefix = "nushell-"
```

Tracking upstream instead would resolve a version that upstream has released but we have not built yet, pinning a URL that does not exist and failing the update. The version pinned has to be one every host can actually download.

***

## `[source]`

`[source]` answers the other question: which file is the artifact. Either name it by templated URL, or glob the assets of a release.

```toml
[source]
url = "https://github.com/cli/cli/releases/download/v${version}/gh_${version}_linux_${arch}.tar.gz"
```

```toml
[source]
github = "pkgforge-dev/Ruffle-AppImage"
glob   = "*${arch}*.appimage"
```

`match` and `exclude` narrow a glob further when a release carries several assets that all match it.

`${version}` and `${arch}` are the only substitutions, and there are no expressions. Anything that cannot be expressed that way goes in a per-host table:

```toml
[source.url]
x86_64-linux  = "https://github.com/Schniz/fnm/releases/download/v${version}/fnm-linux.zip"
aarch64-linux = "https://github.com/Schniz/fnm/releases/download/v${version}/fnm-arm64.zip"
```

### `[source.install]`

What the package takes out of its artifact, written as archive path to installed path. Leave it out entirely when the artifact is the package, as a bare AppImage is.

```toml
[source.install]
"*/rg"               = "bin/rg"
"*/COPYING"          = "COPYING"
"*/doc/rg.1"         = "share/man/man1/rg.1"
"*/complete/rg.fish" = "share/fish/vendor_completions.d/rg.fish"
```

The destination is a path inside the package directory, so the directory it lands in says what the file is. `bin/` is a command, `share/man/` a manual page, `share/fish/vendor_completions.d/` a completion. Omit the destination and it defaults to `bin/` plus the file's own name.

A host may be named for a package whose artifacts are not laid out alike everywhere, which happens when one host is served by a build of our own and the rest come from upstream:

```toml
[source.install]
"nu-${version}-${arch}-unknown-linux-musl/nu" = "bin/nu"

[source.install.riscv64-linux]
"nu" = "bin/nu"
```

Naming a host replaces the shared list for that host alone. Every other host keeps it, so the common case stays written once.

The long form exists for the two things the short one cannot say: extra names for the same file, and an artifact that is itself the file.

```toml
[[source.install]]
from = "License.txt"
to   = "License.txt"

[[source.install]]
from       = "7zz"
to         = "bin/7zz"
symlink_as = ["7z", "7za", "7zr"]
```

```toml
[[source.install]]
to         = "bin/dunst"
symlink_as = ["dunstctl", "dunstify"]
```

An alias is created beside its target and inherits its meaning from the directory, exactly as `to` does. An entry with no `from` means the artifact is the file, which is how a bare binary or a single AppImage is installed under a chosen name.

***

## `[[extra]]`

A side file the artifact does not carry, almost always a licence.

```toml
[[extra]]
url = "https://raw.githubusercontent.com/junegunn/fzf/master/LICENSE"
to  = "LICENSE"
verify = false
```

| Field | Notes |
|---|---|
| `url` | Fetched from upstream. |
| `license` | Or taken from the repository's `licenses/` directory by SPDX id, instead of `url`. |
| `to` | Where it lands in the package directory. |
| `verify` | Whether to pin the content. Defaults to `true`. |

Set `verify = false` for a file that legitimately changes without a version bump, which is the normal case for a licence served from a branch rather than a tag. A pinned hash would turn an upstream copyright-year edit into a failed download for everyone installing that version, and a licence is documentation rather than something that runs.

## Licences

A licence is shipped when the project has one to ship.

* If the archive contains it, `[source.install]` takes it out.
* If not, `[[extra]]` fetches it.
* For the GPL family the text is verbatim by requirement, so one shared copy is the same text every project ships. `license = "GPL-2.0"` takes it from `licenses/` instead of fetching, which is what saves a package whose upstream host rate-limits or whose source repository is gone. This does not apply to MIT, BSD, ISC or similar, whose text carries a per-project copyright line, so only the project's own file will do.
* Proprietary software usually has no licence file at all, only terms on a web page. That belongs in `note` as a link, not fetched and saved as `LICENSE`.
