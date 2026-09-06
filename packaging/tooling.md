---
icon: wrench
description: The sbuild CLI
---

# Tooling

[`sbuild`](https://github.com/pkgforge/sbuilder) is the tool for the soarpkgs tree. One binary, six commands, no state of its own. It turns a [recipe](recipe.md) into a [version file](version-file.md), and the whole tree into the index Soar reads.

## Install

Statically linked, no dependencies:

```bash
curl -fsSL "https://github.com/pkgforge/sbuilder/releases/download/nightly/sbuild-$(uname -m)-linux" -o sbuild
chmod +x sbuild
```

Built for `x86_64`, `aarch64` and `riscv64`, each with a `.b3sum` beside it. Or `cargo install --git https://github.com/pkgforge/sbuilder`.

## Commands

Every command takes the tree root as its first argument, defaulting to `.`.

### `new`

Scaffold a recipe, so a new package starts from something that parses.

```bash
sbuild new ripgrep BurntSushi/ripgrep --type static
```

### `resolve`

Ask each upstream what its current version is, and write the version file that pins it: the URL per host, plus whatever digest the forge already reports.

```bash
sbuild resolve                      # every package
sbuild resolve . ripgrep fzf        # only these
```

This is one API call per package, so it needs `GITHUB_TOKEN` for anything beyond a handful. Re-resolving an unchanged package rewrites nothing.

### `hashfill`

Most forges report a sha256 for an asset. None report blake3, which is what Soar verifies against. This downloads whatever is pinned without a hash beside it, streaming the body so memory stays flat regardless of artifact size.

```bash
sbuild hashfill --jobs 12
```

Run it after `resolve` and before committing. A pinned URL with no hash is the one state `validate` refuses.

### `validate`

Check the tree. Every pinned URL has a hash, every install target stays inside the package directory, every recipe parses and says what it must.

```bash
sbuild validate
```

This is the gate in CI, and the only thing that has to pass before a merge.

### `audit`

Download each archive and check that every path the recipe installs actually resolves inside it. `validate` cannot see this: it reads the tree, and whether `bin/foo` exists in a tarball is a fact about the tarball.

```bash
sbuild audit --host x86_64-linux --host aarch64-linux
```

Slow and network bound by design, so it runs on its own rather than on every merge.

### `meta`

Generate the index for one host, out of the tree and nothing else. No network, no build state. The same tree in gives the same index out, which is why it needs no runner of the architecture it generates for.

```bash
sbuild meta --arch riscv64-linux --output metadata-riscv64-linux.json
```

Soar reads this after `soar json2db` turns it into SQLite. See [metadata](../repositories/soarpkgs/metadata.md) for what the published index looks like.

## Working on a package locally

```bash
git clone --filter=blob:none https://github.com/pkgforge/soarpkgs
cd soarpkgs

sbuild new mypkg owner/repo --type static
$EDITOR packages/mypkg/pkg.toml

sbuild resolve . mypkg
sbuild hashfill
sbuild validate
sbuild audit . mypkg --host x86_64-linux
```

A blobless clone is worth it here. The tree is mostly small text files but has a long history.
