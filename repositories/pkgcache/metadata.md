---
icon: brackets-curly
description: Metadata Spec
---

# Metadata

The Best way to learn it, is to view it ([**https://meta.pkgforge.dev/pkgcache/**](https://meta.pkgforge.dev/pkgcache/)) & and then read the sections below:

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

//Contains the Canonical Build Target [$(uname -m)-$(uname -s)]: https://docs.pkgforge.dev/sbuild/specification/20.x_exec#host
host: "@string",

//Contains the Rank (Generated from Pull count: https://github.com/orgs/pkgforge/packages), Lower rank == More Popular (Downloads/Installs)
//If the value is -1, it implies no rank
rank: "@string",

//Contains the Name of the $PKG itself, this is NOT what it will/should be Installed as
pkg: "@string",

//Contains the Main Family, the package is a part of
pkg_family: "@string",

//Contains the Application ID, generated from source URL [Otherwise Empty/Non-Existent]
//IF THIS IS MISSING, assume pkg_id==app_id
pkg_id: "@string",

//Contains the real name, the $PKG will be installed as, IF THIS IS MISSING, use .pkg
pkg_name: "@string",

//Contains the Package Type: https://docs.pkgforge.dev/sbuild/specification/2.pkg
pkg_type: "@string",

//Contains the Web Index generated at: https://pkgs.pkgforge.dev/
pkg_webpage: "@string",

//Contains the Application ID, usually from appstream files, [Otherwise Empty/Non-Existent]
//IF THIS IS MISSING, DO NOT SET app_id==pkg_id (NOT SAME)
app_id: "@string"

//Contains the URL to Appstream ({AppData/Metainfo}.xml) File of the $PKG/$PKG_FAMILY 
//This MAY BE INACCURATE [Otherwise Empty/Non-Existent]
appstream: "@string",

//Contains the $PKG/$PKG_FAMILY's Category in FreeDesktopSpec [Fallbacks to Utility]
category: "@array",

//Contains the Description of the $PKG/$PKG_FAMILY
description: "@string",

//Contains the URL to .Desktop File of the $PKG/$PKG_FAMILY
//This MAY BE INACCURATE, [Otherwise Empty/Non-Existent]
desktop: "@string",

//Contains the Website/Project Page URL of the $PKG/$PKG_FAMILY [Otherwise Empty/Non-Existent]
homepage: "@array",

//Contains the Logo/Icon File of the $PKG/$PKG_FAMILY (MAY BE INACCURATE) [Fallbacks to Generic Icon]
icon: "@string",

//Contains the License for the $PKG/$PKG_FAMILY (MAY BE INACCURATE) [Otherwise Empty/Non-Existent]
license: "@array",

//Contains the SBUILD Maintainer of the $PKG/$PKG_FAMILY [Otherwise Empty/Non-Existent]
maintainer: "@array",

//Contains Additional Notes,Refs,Info the user need to be aware of, [Otherwise Empty/Non-Existent]
note: "@array",

//Contains names of ALL $PKGs provided (output) from the same SBUILD/$PKG_FAMILY 
//Only if they belong to same $PKG_FAMILY, of the $PKG/$PKG_FAMILY [Otherwise Empty/Non-Existent]
//The values may contain `:` or `==`, details: https://docs.pkgforge.dev/sbuild/specification/16.provides
provides: "@array",

//Contains the Repology Package Slug (https://repology.org/projects/) of the $PKG/$PKG_FAMILY [Otherwise Empty/Non-Existent]
repology: "@array",

//Contains Repology Metadata from /api/v1/project/{$PKG/$PKG_FAMILY} [Otherwise Empty/Non-Existent]
repology: "@array",

//Contains an Array of Screenshots of the $PKG/$PKG_FAMILY (MAY BE INACCURATE) [Otherwise Empty/Non-Existent]
screenshots: "@array",

//Contains the Github/Gitlab/$GIT_SRC URL of the $PKG/$PKG_FAMILY [Otherwise Empty/Non-Existent]
src_url: "@array",

//Contains Tags describing/categorizing the $PKG/$PKG_FAMILY [Otherwise Empty/Non-Existent]
tag: "@array"

//Contains the version of the $PKG
//If starts with ^HEAD- , then implies it was built from source
version: "@string",

//Contains the upstream (Git release/tag) version of the $PKG
//This serves as a fallback to compare/show version if `.version` is `HEAD-` or empty
version_upstream: "@string",

//Contains the Exact Blake3sum of the $PKG
bsum: "@string",

//Contains the Exact Date the $PKG was Built/Fetched & Uploaded
//Format in YYYY-MM-DDTHH:MM:SS (example: 2024-10-08T01:19:56)
build_date: "@string",

//Contains the Github Actions Run URL that built the ${PKG}
//If starts with ^local:// , then it implies it was built by a maintainer on a dev machine
build_gha: "@string",

//Contains the Github Actions Run ID that built the ${PKG}
//If .build_gha started with ^local:// , then it implies it was built by a maintainer on a dev machine, thus this value is just: /etc/machine-id
build_id: "@string",

//Contains the link to view the Actual CI BUILD LOG of the $PKG
build_log: "@string",

//Contains the SBUILD Script the $BINARY was Built/Fetched With
//Is usually a `blob url`, might require replacing with `raw`
build_script: "@string",

//Contains the Total Downloads (Pulls) a $PKG has received (ghcr pull)
//If the value is -1, it implies no data was available
download_count: "@string",
//Similar fields like `download_count_month`, `download_count_week` may also be available

//Contains the Raw Direct Download URL of the $PKG
//This is a ghcr api call, so may not be as relaible as `pull`
download_url: "@string",

//Contains the Github Registry Container (ghcr) Name + Blob Digest of the $PKG
//This can be `pulled` directly by an OCI client (Pulls only $PKG)
ghcr_blob: "@array",

//Contains All the artifacts that can be pulled from the $ghcr_pkg
//This is essentially a list of ALL org.opencontainers.image.title
ghcr_files: "@array",

//Contains the Github Registry Container (ghcr) Name + Tag of the $PKG
//This can be `pulled` directly by an OCI client
ghcr_pkg: "@string",

//Contains the Total Size of all Layers that can be pulled from the $ghcr_pkg
//This adds total size of all artifacts & is in Human Readable [KiB MiB GiB BUT written as KB MB GB (Example: 9.01 MB)]
ghcr_size: "@string",

//Essentially the raw BYTE size version of $ghcr_size
ghcr_size_raw: "@string",

//Contains browser registry URL of the $PKG (Github Registry Container Name)
ghcr_url: "@string",

//Contains the Raw Container Manifest Download URL of the $ghcr_pkg
//This is a ghcr api call, so may not be as relaible as `manifest fetch`
manifest_url: "@string",

//Contains the Exact Sha256sum of the $PKG <AUTOGENERATED>
shasum: "@string",

//Contains the Total Size of the $PKG in Human Readable [KiB MiB GiB BUT written as KB MB GB (Example: 9.01 MB)]
//This contains ONLY the size of $PKG from a $ghcr_pkg & NOT ALL Artifacts
size: "@string",

//Essentially the raw BYTE size version of $ghcr_size
size_raw: "@string",

//Contains an Array of Tags of the $ghcr_pkg [Otherwise Empty/Non-Existent]
//This often contains the tag for the $PKG itself at .snapshots[0] & other values are previous tags/versions
snapshots: "@array",
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
[**R2**](https://meta.pkgforge.dev/pkgcache/) (99% Uptime) \[<mark style="color:green;">**RECOMMENDED**</mark>]

```bash
https://meta.pkgforge.dev/pkgcache/${HOST}.json
```
{% endhint %}

{% hint style="info" %}
[**Github**](https://github.com/pkgforge/metadata/tree/main/pkgcache/data) \[<mark style="color:orange;">**Fallback**</mark>]

{% code overflow="wrap" %}
```bash
https://raw.githubusercontent.com/pkgforge/metadata/main/pkgcache/data/${HOST}.json
```
{% endcode %}
{% endhint %}

{% hint style="warning" %}
[**HF**](https://huggingface.co/datasets/pkgforge/pkgcache/tree/main) (<mark style="color:orange;">**Sometimes goes Down**</mark>)

* <mark style="color:blue;">https://hf.pkgcache.bincache.pkgforge.dev/</mark><mark style="color:orange;">${PATH}</mark> is just a redirect to <mark style="color:blue;">https://huggingface.co/datasets/pkgforge/pkgcache/resolve/main/</mark><mark style="color:orange;">${PATH}</mark>

{% code overflow="wrap" %}
```bash
https://hf.pkgcache.pkgforge.dev/${HOST}/METADATA.json
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
#Simple example to: List all ghcr_pkg of All Pkgs
curl -qfsSL "https://meta.pkgforge.dev/pkgcache/$(uname -m)-$(uname -s).json" | jq -r '.[] | .ghcr_pkg'

#To pretty print anything that matches qbittorrent from .pkg
curl -qfsSL "https://meta.pkgforge.dev/pkgcache/$(uname -m)-$(uname -s).json" \
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
