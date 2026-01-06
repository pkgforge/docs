---
icon: brackets-curly
description: Metadata Spec
---

# Metadata

Soarpkgs generates metadata for prebuilt packages:
- **bincache**: Static binaries
- **pkgcache**: GUI applications

## URLs

{% hint style="info" %}
* Add `.zstd` for compressed versions
* Formats: `.json`, `.sdb` (sqlite), `.sdb.zstd`
* `${HOST}` = `aarch64-Linux`, `x86_64-Linux`
{% endhint %}

```
https://github.com/pkgforge/soarpkgs/releases/latest/download/bincache-${HOST}.json
https://github.com/pkgforge/soarpkgs/releases/latest/download/pkgcache-${HOST}.json
```

## Fields

{% code overflow="wrap" %}
```json5
// @string --> Single String Value
// @array --> Multiple (array) String Values

// Package identification
disabled: "false",         // If true, package is broken
host: "@string",           // Build target (arch-os)
pkg: "@string",            // Package name
pkg_family: "@string",     // Package family
pkg_id: "@string",         // Package ID
pkg_name: "@string",       // Install name (fallback to pkg)
pkg_type: "@string",       // Package type
pkg_webpage: "@string",    // Web index page

// App metadata
app_id: "@string",         // Application ID
appstream: "@string",      // Appstream XML URL
category: "@array",        // FreeDesktop categories
description: "@string",    // Package description
desktop: "@string",        // Desktop file URL
homepage: "@array",        // Project homepage
icon: "@string",           // Icon file
license: "@array",         // License info
maintainer: "@array",      // SBUILD maintainer
note: "@array",            // Additional notes
provides: "@array",        // Provided binaries
repology: "@array",        // Repology mapping
screenshots: "@array",     // Screenshots
src_url: "@array",         // Source URLs
tag: "@array",             // Tags

// Version info
version: "@string",        // Package version (HEAD- = built from source)
version_upstream: "@string", // Upstream version

// Build info
bsum: "@string",           // Blake3sum
build_date: "@string",     // Build date (YYYY-MM-DDTHH:MM:SS)
build_gha: "@string",      // GitHub Actions run URL
build_id: "@string",       // Build ID
build_log: "@string",      // Build log URL
build_script: "@string",   // SBUILD script URL

// GHCR info
download_url: "@string",   // Direct download URL
ghcr_blob: "@array",       // GHCR blob digest
ghcr_files: "@array",      // Artifacts in package
ghcr_pkg: "@string",       // GHCR package name + tag
ghcr_size: "@string",      // Total size (human readable)
ghcr_size_raw: "@string",  // Total size (bytes)
ghcr_url: "@string",       // Registry URL
shasum: "@string",         // SHA256sum
size: "@string",           // Package size (human readable)
size_raw: "@string",       // Package size (bytes)
snapshots: "@array"        // Version tags
```
{% endcode %}

## JQ Examples

```bash
# List all packages
curl -qfsSL "https://github.com/pkgforge/soarpkgs/releases/latest/download/bincache-$(uname -m)-$(uname -s).json" | jq -r '.[] | .pkg'

# Search for a package
curl -qfsSL "https://github.com/pkgforge/soarpkgs/releases/latest/download/bincache-$(uname -m)-$(uname -s).json" | jq -r '.[] | select(.pkg | test("qbittorrent"; "i"))'
```

## Security

Metadata is generated in [pkgforge/soarpkgs](https://github.com/pkgforge/soarpkgs). Verify provenance via [GitHub Attestations](https://github.com/pkgforge/soarpkgs/attestations).
