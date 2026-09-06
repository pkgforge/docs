---
icon: lock
description: The pinned release
---

# Version file

`<name>-<version>.toml` is one release of a package, written out literally. There are no templates and nothing to resolve. This is the file a reviewer reads, and the source of everything the published index says about a release.

It is written by `sbuild resolve` and `sbuild hashfill` rather than by hand, but it is committed and reviewed like anything else, which is the point of the format.

```toml
version = "2.96.0"
date    = "2026-08-14T09:12:03Z"

[url]
x86_64-linux  = "https://github.com/cli/cli/releases/download/v2.96.0/gh_2.96.0_linux_amd64.tar.gz"
aarch64-linux = "https://github.com/cli/cli/releases/download/v2.96.0/gh_2.96.0_linux_arm64.tar.gz"

[blake3]
x86_64-linux  = "..."
aarch64-linux = "..."

[sha256]
x86_64-linux  = "..."
aarch64-linux = "..."

[size]
x86_64-linux  = 14652560
aarch64-linux = 13980112
```

| Table | Notes |
|---|---|
| `version` | The resolved version, with any `strip-prefix` already removed. |
| `date` | When upstream published the release. Recorded because a version built from a commit hash carries no order of its own, so a client comparing two snapshots has nothing else to go on. |
| `[url]` | The artifact, per host. |
| `[blake3]` | What Soar verifies a download against. It can only be obtained by fetching the artifact, which is what `sbuild hashfill` does. |
| `[sha256]` | What the forge API already reports for an asset, so it doubles as a cross-check against a release's own checksums file. |
| `[size]` | Bytes, per host. |

Every host-keyed table is ordered by `[url]`, so a file only changes when what it pins changes. Anything else would churn a diff on every run and bury the one line somebody needs to review.

***

## Side files

`[[extra]]` entries are pinned per version, because most licence URLs point at a branch and their content can change without a release. Pinning them here means a change shows up as a diff on the next bump rather than silently.

```toml
[[extra]]
url    = "https://raw.githubusercontent.com/cli/cli/master/LICENSE"
to     = "LICENSE"
blake3 = "..."
sha256 = "..."
```

`host` is set when the file differs per host, as an upstream's per-architecture side file does. Absent means it applies to every host, which is the case for a licence. A file whose recipe set `verify = false` is pinned by URL but carries no hash.

***

## Overrides

`note` and `provides` may be restated here for this version alone, replacing rather than merging with what `pkg.toml` says. They are the two that realistically change between releases:

```toml
note = ["Requires a GPU driver supporting Vulkan 1.3 from this release on"]
```

***

## Several versions at once

A package directory may hold more than one version file. Each becomes its own entry in the generated index, so an older release stays installable after a newer one is pinned, and `soar install pkg@version` can reach it.
