---
icon: brackets-curly
description: The published index
---

# Metadata

soarpkgs publishes one index per host, generated from the tree by `sbuild meta` and converted to SQLite by `soar json2db`. Generation reads the tree and nothing else. No network, no build state, so the same tree always produces the same index, which is what makes the published file auditable.

## URLs

Everything is published on the [latest release](https://github.com/pkgforge/soarpkgs/releases/latest):

```
https://github.com/pkgforge/soarpkgs/releases/latest/download/metadata-${HOST}.sdb.zstd
https://github.com/pkgforge/soarpkgs/releases/latest/download/metadata-${HOST}.json
```

{% hint style="info" %}
* `${HOST}` is `x86_64-linux`, `aarch64-linux` or `riscv64-linux`
* Available as `.json` and `.sdb` (SQLite), each also with a `.zstd` variant
* Every file has a `.sig` beside it, a minisign signature over that exact file
{% endhint %}

Soar uses the `.sdb.zstd` variant by default, since it is what it reads directly. The JSON is there for anything else that wants to consume the index.

## Shape

```json
{
  "format": 1,
  "packages": [ ... ]
}
```

`format` is the index format version, published so a client can tell an index it cannot read from one that merely lacks a field, and say which of the two it is. Soar currently understands format `1`, and refuses anything higher rather than guessing.

## Fields

One entry is a single package at a single version. A package with several pinned versions contributes one entry each.

{% code overflow="wrap" %}
```json5
{
  // Identity
  "pkg_name":    "string",    // the name a user installs
  "pkg_family":  "string",    // only when the recipe states one
  "pkg_type":    "string",    // the format of the artifact, e.g. static, appimage, onelf
  "description": "string",
  "version":     "string",
  "date":        "string",    // when upstream published this release, RFC 3339

  // The artifact
  "download_url": "string",
  "size":         0,          // bytes
  "bsum":         "string",   // blake3, what soar verifies against
  "shasum":       "string",   // sha256, as the forge reported it

  // Metadata
  "src_url":    ["string"],   // upstream repository
  "homepage":   ["string"],
  "license":    ["string"],   // SPDX identifiers
  "maintainer": ["string"],
  "category":   ["string"],   // FreeDesktop categories
  "repology":   ["string"],
  "note":       ["string"],

  // What gets installed
  "files": [                  // absent means the artifact is the package
    { "source": "*/rg", "to": "bin/rg", "alias": [] }
  ],
  "extra": [                  // side files the artifact does not carry
    { "url": "string", "to": "LICENSE", "blake3": "string", "sha256": "string" }
  ]
}
```
{% endcode %}

Empty lists and absent values are left out rather than written as nulls, so a field you do not see is a field the package does not set.

`files` entries take their meaning from where they land. `bin/` is a command, `share/man/` a manual page. `alias` holds extra names for the same file, created beside it.

## Reading it

```bash
BASE="https://github.com/pkgforge/soarpkgs/releases/latest/download"
HOST="$(uname -m)-linux"

# every package name
curl -qfsSL "${BASE}/metadata-${HOST}.json" | jq -r '.packages[].pkg_name'

# one package, in full
curl -qfsSL "${BASE}/metadata-${HOST}.json" | jq '.packages[] | select(.pkg_name == "ripgrep")'

# search by name or description
curl -qfsSL "${BASE}/metadata-${HOST}.json" \
  | jq '.packages[] | select((.pkg_name + " " + .description) | test("torrent"; "i"))'
```

## Verifying

```bash
BASE="https://github.com/pkgforge/soarpkgs/releases/latest/download"
HOST="x86_64-linux"

curl -qfsSLO "${BASE}/metadata-${HOST}.json"
curl -qfsSLO "${BASE}/metadata-${HOST}.json.sig"
curl -qfsSLO "https://raw.githubusercontent.com/pkgforge/soarpkgs/main/keys/minisign.pub"

minisign -V -p minisign.pub -m "metadata-${HOST}.json"
```

Soar does this for you, with the public key built in. Signature verification can be turned off per repository in the [config](../external/), which you should only do for a repository that publishes none.
