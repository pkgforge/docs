---
description: Metadata Spec
icon: brackets-curly
---

# Metadata

The Best way to learn it, is to view it ([**https://meta.pkgforge.dev/soarpkgs/INDEX.json**](https://meta.pkgforge.dev/soarpkgs/INDEX.json)) & and then read the sections below:

### Fields

```json5
//The Structure is like:
 [
   {
   ...objects...
   }
 ]
```

{% code overflow="wrap" %}
```json5
// @string --> Single String Value
// @array --> Multiple (array) String Values
// @array|@string --> Can be either, check & handle accordingly

//Denotes if this pkg is disabled (currently broken, SHOULD NOT BE INSTALLED)
disabled: "false", //if true, then this pkg is marked disabled
//If disabled == "true", then it may also contain (Optionally)
disabled_reason: "@array|@string" //https://docs.pkgforge.dev/sbuild/specification/1.shebang

//Contains the Name of the $PKG itself, this is NOT what it will/should be Installed as, this is same as pkg_name (If compared with bincache/pkgcache's metadata)
pkg: "@string",

//Contains the Main Family, the package is a part of
pkg_family: "@string",

//Contains the Application ID, generated from source URL [Otherwise Empty/Non-Existent]
//IF THIS IS MISSING, assume pkg_id==app_id
pkg_id: "@string",

//Contains the Package Type: https://docs.pkgforge.dev/sbuild/specification/2.pkg
pkg_type: "@string",

//Contains the Application ID, usually from appstream files, [Otherwise Empty/Non-Existent]
//IF THIS IS MISSING, DO NOT SET app_id==pkg_id (NOT SAME)
app_id: "@string"

//Contains the Github Registry Container (ghcr) Name of the $PKG built for bincache
//This can be compared directly with bincache's metadata & allows download/install of prebuilt artifacts
//If this is Empty/Non-Existent, check for `.pkgcache`
bincache: "@string",

//Contains the URL to the SBUILD Script
//Is usually a `blob url`, might require replacing with `raw`
build_script: "@string",

//Contains the $PKG/$PKG_FAMILY's Category in FreeDesktopSpec [Fallbacks to Utility]
category: "@array",

//Contains the Description of the $PKG/$PKG_FAMILY
description: "@array|@string",

//Contains the Distro Packages of the $PKG/$PKG_FAMILY
distro_pkg: "@array",

//Contains the Raw Direct URL of the $SBUILD
//This is a redirector using Cloudflare workers, It can also be created by simply replacing `blob` with `raw` from build_script
download_url: "@string",

//Contains the Website/Project Page URL of the $PKG/$PKG_FAMILY [Otherwise Empty/Non-Existent]
homepage: "@array",

//Contains the Canonical Build/Install Targets [$(uname -m)-$(uname -s)]: https://docs.pkgforge.dev/sbuild/specification/20.x_exec#host
host: "@array",

//Contains the Logo/Icon File of the $PKG/$PKG_FAMILY (MAY BE INACCURATE) [Fallbacks to Generic Icon]
icon: "@string",

//Contains the License for the $PKG/$PKG_FAMILY (MAY BE INACCURATE) [Otherwise Empty/Non-Existent]
license: "@array",

//Contains the SBUILD Maintainer of the $PKG/$PKG_FAMILY [Otherwise Empty/Non-Existent]
maintainer: "@array",

//Contains Additional Notes,Refs,Info the user need to be aware of, [Otherwise Empty/Non-Existent]
note: "@array",

//Contains the Github Registry Container (ghcr) Name of the $PKG built for pkgcache
//This can be compared directly with pkgcache's metadata & allows download/install of prebuilt artifacts
//If this is Empty/Non-Existent, check for `.bincache`
pkgcache: "@string",

//Contains the WebIndex generated at: https://pkgs.pkgforge.dev/
pkg_webpage: "@string",

//Contains names of ALL $PKGs provided (output) from the same SBUILD/$PKG_FAMILY 
//Only if they belong to same $PKG_FAMILY, of the $PKG/$PKG_FAMILY [Otherwise Empty/Non-Existent]
//The values may contain `:` or `==`, details: https://docs.pkgforge.dev/sbuild/specification/16.provides
provides: "@array",

//Contains Repology Metadata from /api/v1/project/{$PKG/$PKG_FAMILY} [Otherwise Empty/Non-Existent]
repology: "@array",

//Contains the Github/Gitlab/$GIT_SRC URL of the $PKG/$PKG_FAMILY [Otherwise Empty/Non-Existent]
src_url: "@array",

//Contains Tags describing/categorizing the $PKG/$PKG_FAMILY [Otherwise Empty/Non-Existent]
tag: "@array"

//Contains the version of the $PKG
//If starts with ^HEAD- , then implies it was built from source
version: "@string"
```
{% endcode %}

***

### URLs

{% hint style="info" %}
* [x] Add (at end)  <mark style="color:orange;">**`.xz`**</mark> OR <mark style="color:orange;">**`.zstd`**</mark> to get Compressed Versions
* [x] Add (at end)<mark style="color:purple;">**`.bsum`**</mark> to get Checksums, useful to check if Remote has Changed
* [x] <mark style="color:purple;">**`${HOST}`**</mark> == <mark style="color:orange;">**`aarch64-Linux`**</mark> ,  <mark style="color:orange;">**`x86_64-Linux`**</mark>  (Case Insensitive)
{% endhint %}

{% hint style="success" %}
[**R2**](https://meta.pkgforge.dev/soarpkgs/) (99% Uptime) \[<mark style="color:green;">**RECOMMENDED**</mark>]

```bash
https://meta.pkgforge.dev/soarpkgs/INDEX.json
```
{% endhint %}

{% hint style="info" %}
[**Github**](https://github.com/pkgforge/metadata/blob/main/soarpkgs/data/INDEX.json) \[<mark style="color:orange;">**Fallback**</mark>]

{% code overflow="wrap" %}
```bash
https://raw.githubusercontent.com/pkgforge/metadata/main/soarpkgs/data/INDEX.json
```
{% endcode %}
{% endhint %}

***

### [JQ](https://jqlang.github.io/jq/manual/)

{% hint style="info" %}
This is a basic example demonstrating how easy it is to work with the Metadata

{% code overflow="wrap" %}
```bash

#Append `| jq -r '.[].$PROPERTY'` to filter them
#Simple example to: List all pkg_id of All Pkgs
curl -qfsSL "https://meta.pkgforge.dev/soarpkgs/INDEX.json" | jq -r '.[] | .pkg_id'

#To pretty print anything that matches qbittorrent from .pkg
curl -qfsSL "https://meta.pkgforge.dev/soarpkgs/INDEX.json" \
| jq -r '
  .[] 
  | select(.pkg | test("qbittorrent"; "i")) 
  | "---------------------------\n" + (
      . 
      | to_entries 
      | map("\(.key): \(.value)") 
      | join("\n")
    )
'
```
{% endcode %}
{% endhint %}

***

### Security

Metadata files are generated at: [https://github.com/pkgforge/metadata](https://github.com/pkgforge/metadata). Generation Provenance can be verified using [GitHub Attestations](https://docs.github.com/en/actions/security-for-github-actions/using-artifact-attestations/using-artifact-attestations-to-establish-provenance-for-builds): [https://github.com/pkgforge/metadata/attestations](https://github.com/pkgforge/metadata/attestations)

