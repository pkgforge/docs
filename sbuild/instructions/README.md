---
icon: wrench
description: How to write an .SBUILD
---

# Instructions

### Prerequisite

*   [x] [**Install&#x20;**<mark style="color:purple;">**`Soar`**</mark>](https://soar.qaidvoid.dev/installation)

    Yes, really. Do it Now: [https://soar.qaidvoid.dev/install](https://soar.qaidvoid.dev/install)
* [x] [**Dependencies** (Host)](#user-content-fn-1)[^1]

{% hint style="info" %}
- [x] [bash](https://command-not-found.com/bash), [b3sum](https://github.com/BLAKE3-team/BLAKE3), [curl](https://curl.se/download.html), [coreutils](https://en.wikipedia.org/wiki/List_of_GNU_Core_Utilities_commands), [file](https://command-not-found.com/file), [findutils (find, xargs)](https://command-not-found.com/find), [fuse3 (fusermount3)](https://command-not-found.com/mount.fuse3), [gettext](https://command-not-found.com/gettext), [grep](https://command-not-found.com/grep), [jq](https://github.com/jqlang/jq),  [sed](https://command-not-found.com/sed), [shellcheck](https://github.com/koalaman/shellcheck), [wget](https://command-not-found.com/wget), [yj](https://github.com/sclevine/yj), [yq](https://github.com/mikefarah/yq)
- [x] Some of these can be installed with [<mark style="color:purple;">**`Soar`**</mark>](https://soar.qaidvoid.dev/installation)

```bash
soar add 'bash/bash#base' \
'b3sum#bin' \
'curl#bin' \
'findutils/find#base' \
'grep/grep#base' \
'jq#bin' \
'sed#bin' \
'shellcheck#bin' \
'findutils/xargs#base' \
'yj#bin' \
'yq#bin' --yes
```

* [x] **But if Possible, Use your Distro's own PKG Manager to avoid breaking stuff**
{% endhint %}

* [x] Read the [<mark style="color:blue;">**`Spec`**</mark>](https://docs.pkgforge.dev/sbuild/specification): [https://docs.pkgforge.dev/sbuild/specification](https://docs.pkgforge.dev/sbuild/specification)
* [x] View [<mark style="color:blue;">**some Examples**</mark>](https://github.com/pkgforge/soarpkgs/tree/main/packages) <mark style="color:blue;">:</mark> [<mark style="color:blue;">https://github.com/pkgforge/soarpkgs/tree/main/packages</mark>](https://github.com/pkgforge/soarpkgs/tree/main/packages)

***

### Write

* [x] Copy the [**Generic Template**](https://github.com/pkgforge/soarpkgs/blob/main/templates/generic.SBUILD.yaml): [https://github.com/pkgforge/soarpkgs/blob/main/templates/generic.SBUILD.yaml](https://github.com/pkgforge/soarpkgs/blob/main/templates/generic.SBUILD.yaml)
* [x] Use the [**Repology Fetcher**](https://github.com/pkgforge/metadata/blob/main/soarpkgs/scripts/repology_fetcher.sh): [https://raw.githubusercontent.com/pkgforge/metadata/main/soarpkgs/scripts/repology\_fetcher.sh](https://raw.githubusercontent.com/pkgforge/metadata/main/soarpkgs/scripts/repology_fetcher.sh)

> {% code overflow="wrap" %}
> ```bash
> !#Assuming You have READ & VERIFIED what the script contains
> source <(curl -qfsSL "https://raw.githubusercontent.com/pkgforge/metadata/main/soarpkgs/scripts/repology_fetcher.sh")
> #The function itself is `repology_fetcher` but is aliased to `repology-fetcher` for convenience
> #If you don't want to source it, just download and save it somewhere in $PATH
>
> !#Run it with the app/pkg_name
> repology-fetcher "pkg_name"
> #Example: repology-fetcher "librewolf"
> ```
> {% endcode %}

* [x] Start Filling in the [**Generic Template**](https://github.com/pkgforge/soarpkgs/blob/main/templates/generic.SBUILD.yaml) by Consulting an [**Example**](examples.md) or the [**SPEC**](broken-reference)
* [x] After you are done, you can validate it using the [**sbuild-linter**](https://github.com/pkgforge/sbuilder): [https://github.com/pkgforge/sbuilder](https://github.com/pkgforge/sbuilder)

> {% code overflow="wrap" %}
> ```sh
> !#Add it using Soar
> soar add "sbuild-linter" "shellcheck"
> #Or Download manually & Add to Path: https://github.com/pkgforge/sbuilder/releases
>
> !#Run it with /path/to/your/SBUILD
> sbuild-linter "./example.SBUILD"
> #If it's not successful, fix your errors
>
> !#To get pkgver
> sbuild-linter "./example.SBUILD" --pkgver
> ```
> {% endcode %}

* [x] If your <mark style="color:purple;">**`SBUILD`**</mark> gets validated successfully, <mark style="color:green;">**Congrats!**</mark> You can now create a [**`Pull Request`**](https://github.com/pkgforge/soarpkgs/compare) or an [**`Issue`**](https://github.com/pkgforge/soarpkgs/issues/new/choose), Remember to **Link/Copy\&Paste** the <mark style="color:orange;">**`.validated`**</mark> version of your <mark style="color:purple;">**`SBUILD`**</mark>

***

### Build

{% hint style="warning" %}
It is recommended you setup a sandbox or containerized environment before running arbitrary SBUILDs that have NOT been approved by a maintainer into [pkgforge/soarpkgs](https://github.com/pkgforge/soarpkgs)
{% endhint %}

* [x] [**Install sbuild**](https://github.com/pkgforge/sbuilder)

```bash
!#Add it using Soar
soar add "sbuild" "shellcheck"
#Or Download manually & Add to Path: https://github.com/pkgforge/sbuilder/releases

!#Run it with /path/to/your/SBUILD
sbuild "./example.SBUILD" --log-level "verbose" --keep --outdir "./SBUILD-TEST"
#If it's not successful, fix your errors
```

[^1]: Only needed if you intend to use the Automation Scripts.\
    Otherwise, you may skip this & just do everything manually
