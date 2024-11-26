---
icon: gear
description: Environment Variables for SBUILDER
---

# ENV\_VARS (SBUILDER)

{% hint style="info" %}
This is internal documentation meant for the **`SBUILDER`**, **not for humans** [writing SBUILD Scripts](broken-reference)
{% endhint %}

* [x] <mark style="color:orange;">**`${SBUILD_SUCCESSFUL}`**</mark>

> - **Description**: If the <mark style="color:blue;">**Build**</mark> Was <mark style="color:green;">**Successful**</mark> or <mark style="color:red;">**Failed**</mark>, if It <mark style="color:red;">**Failed**</mark> (<mark style="color:orange;">**`SBUILD_SUCCESSFUL`**</mark>**`==`**<mark style="color:red;">**`false`**</mark>) **Bail & Exit Immediately (Still Copy all Dirs to&#x20;**<mark style="color:orange;">**`SOAR_CACHE`**</mark>**)**
> - **Values**: <mark style="color:green;">**`true`**</mark> | <mark style="color:red;">**`false`**</mark>

* [x] <mark style="color:orange;">**`${SBUILD_PKG}`**</mark>

> - **Description**: The <mark style="color:blue;">**Package Name**</mark>, used as <mark style="color:blue;">**Prefix**</mark> for [**ALL NEEDED Files**](needed_files.md) <<mark style="color:green;">**ALWAYS**</mark> Available>
> - **Value**: [<mark style="color:purple;">**`.pkg+.pkg_type`**</mark>](../specification/2.pkg.md)
> - Also used as **default&#x20;**<mark style="color:blue;">**OutputDir**</mark>**&#x20;if** <mark style="color:orange;">**`-o | --output`**</mark><mark style="color:blue;">**`PATH`**</mark> was **NOT Specified** (**ONLY IF** <mark style="color:orange;">**`SBUILD_SUCCESSFUL`**</mark>**`==`**<mark style="color:green;">**`true`**</mark>)

* [x] <mark style="color:orange;">**`${PKG_TYPE}`**</mark>

> - **Description**: One of <mark style="color:purple;">**`appbundle|appimage|archive|dynamic|flatimage|gameimage|nixappimage|runimage|static`**</mark>
> - **ALWAYS Re-Checked** using _Magic Bytes_ for _Utmost Sanity_
> - <mark style="color:purple;">**`dynamic|static`**</mark> are [**binaries (cli)**](../../formats/binaries/), _don't need Integration (Desktop,Icons etc)_
> - <mark style="color:red;">**`UNKNOWN`**</mark> means, the [<mark style="color:purple;">**`pkg_type`**</mark>](../specification/2.pkg.md) value was empty, **Rechecked anyway**

* [x] <mark style="color:orange;">**`${SBUILD_OUTDIR}`**</mark>

> - **Description**: The **Root** (<mark style="color:orange;">**Temporary**</mark>) <mark style="color:blue;">**Working Directory**</mark> [<mark style="color:purple;">**`x_exec.run`**</mark>](../specification/20.x_exec.md) is Run From <<mark style="color:green;">**ALWAYS**</mark> _Available_>
> - **All** [**NEEDED Files**](needed_files.md) **must exist in this&#x20;**<mark style="color:orange;">**Directory**</mark>
> - This <mark style="color:blue;">**Directory**</mark> is moved to <mark style="color:orange;">**`SOAR_CACHE`**</mark> oafter Build Finishes (Regradless if Successful | Failed)  but **only&#x20;**<mark style="color:blue;">**depth 1**</mark>**&#x20;unless used** <mark style="color:orange;">**`-k | --keep`**</mark> **which would move the entire directory** including <mark style="color:orange;">**`${SBUILD_TMPDIR}`**</mark>(**PATH**: <mark style="color:orange;">**`${SBUILD_OUTDIR}/`**</mark><mark style="color:purple;">**`SBUILD_TEMP`**</mark>)
> - After moving to <mark style="color:orange;">**`SOAR_CACHE`**</mark> , it is _also copied to_ <mark style="color:blue;">**OutputDir**</mark> **ONLY IF** <mark style="color:orange;">**`SBUILD_SUCCESSFUL`**</mark>**`==`**<mark style="color:green;">**`true`**</mark>specified using <mark style="color:orange;">**`-o | --output`**</mark><mark style="color:blue;">**`PATH`**</mark>, otherwise this is copied to <mark style="color:orange;">**`${CWD}/${SBUILD_PKG}`**</mark> <mark style="color:blue;">**directory**</mark>.
> - if <mark style="color:orange;">**`SBUILD_SUCCESSFUL`**</mark>**`==`**<mark style="color:red;">**`false`**</mark> , don't copy it to <mark style="color:blue;">**OutputDir**</mark> , fetch the logs & show errors along with printing realpath to <mark style="color:orange;">**`SOAR_CACHE`**</mark><mark style="color:blue;">**Dir**</mark>

* [x] <mark style="color:orange;">**`${SBUILD_TMPDIR}`**</mark>

> - **Description**: The <mark style="color:purple;">**SBUILD\_TEMP**</mark> <mark style="color:blue;">**Directory**</mark> inside <mark style="color:orange;">**${SBUILD\_OUTDIR}**</mark> (**PATH**: <mark style="color:orange;">**`${SBUILD_OUTDIR}/`**</mark><mark style="color:purple;">**`SBUILD_TEMP`**</mark>), used for storing _NON-NEEDED_ Files <<mark style="color:green;">**ALWAYS**</mark> _Available_>
> - This **dir is cleaned** (_**Not Copied**_ to <mark style="color:orange;">**`SOAR_CACHE`**</mark>) **by Default** **unless used** <mark style="color:orange;">**`-k | --keep`**</mark>
> - **If rebuilding**, & _this dir already exists_ (User used <mark style="color:orange;">**`-k | --keep`**</mark>during **prevous build**), it is **cleaned/purged** with <mark style="color:orange;">**`--clean-build`**</mark> or <mark style="color:orange;">**`-c | --clean`**</mark>

* [x] <mark style="color:orange;">**`${SBUILD_META}`**</mark>

> - **Description**: **JSON Metadata file**, available at <mark style="color:orange;">**`${SBUILD_OUTDIR}/${SBUILD_PKG}.json`**</mark>
> - This is **auto created** by the <mark style="color:purple;">**SBUILDER**</mark> at the end of a **BUILD (**<mark style="color:orange;">**`SBUILD_SUCCESSFUL`**</mark>**`==`**<mark style="color:green;">**`true`**</mark>**)**

<pre class="language-json5" data-overflow="wrap"><code class="lang-json5">// This json resembles same format as: https://soarpkgs.pkgforge.dev/metadata/METADATA.json
// Replace &#x26; Fill based on the fields from SBUILD
// Values enclosed in [] indicate that they are an array
// Values that are $UPPERCASE indicate they are Variables, and their values need to be replaced
// Certain Fields like build_util, distro_pkg etc are not added in the metadata
{
//Will always exist (linter would exit if Empty)
 "_disabled": "._disabled",
//Will always exist (linter would exit if Empty)
 "pkg": ".pkg",
//Will always exist (linter would create it if Empty)
 "pkg_id": ".pkg_id",
//Empty Value, if SBUILD didn't have it
 "app_id": ".app_id",
//Will always exist (Use Magic Byte to determine if Empty)
 "pkg_type": ".pkg_type",
//Will always exist (linter would exit if Empty)
 "description": ".description",
<strong>//Empty Value, if SBUILD didn't have it
</strong> "note": "[.note]",
//Fetch from $SBUILD_OUTDIR/$pkg.version, if empty, create based on date as YYYYMMDD-HHMMSS (Example --> 20241126-062034)
 "version": "$PKG_VERSION",
//This field would be pre-populated if user uses the pkgforge-community Repo (SoarPkgs)
 "download_url": "https://soarpkgs.pkgforge.dev/packages/$FILENAME_OF_SBUILD_INPUT_FILE",
//Calculated, in KiB|MiB|GiB format: 1KB, 10MB, 100GB
 "size": "$SIZE_OF_$PKG",
//Calculated 
 "bsum": "$B3SUM_OF_$PKG",
<strong>//Calculated, needed since b3sum is not a coreutil yet 
</strong> "shasum": "$SHA256SUM_OF_$PKG",
//Format: YYYY-MM-DDTHH:MM:SS (example: 2024-10-08T01:19:56) 
 "build_date": "$BUILD_DATE",
//Empty Value, if SBUILD didn't have it 
 "repology": "[.repology]",
//Will always exist (linter would exit if Empty) 
 "src_url": "[.src_url]",
//Will always exist (linter would create it if Empty) 
 "homepage": "[.homepage]", 
//If this was a local build, just point to local dir where the .SBUILD is stored
//The Validated SBUILD file that built it, will copy it to install dir after installation) 
 "build_script": "https://github.com/pkgforge/soarpkgs/blob/main/packages/ $VALID_PKGSRC",
//points to local dir where the $pkg.log is stored
//The log file is saved to install dir after installation or in the OutDir
 "build_log": "$PATH_TO_LOCAL_BUILD.log",
//Empty Value, if SBUILD didn't have it 
 "appstream": ".appstream",
//Will always exist (linter would create it if Empty) 
 "category": "[.category]",
//Depending on Package type, may or may not exist, handled logically 
 "desktop": "$PKG.desktop",
//Depending on Package type, may or may not exist, handled logically, using default icon as fallback 
 "icon": "$PKG.{DirIcon|png|Svg}",
//Empty Value, if SBUILD didn't have it 
 "license" : "[.license]",
//Empty Value, if SBUILD didn't have it 
 "provides": "[.provides]",
//Empty, if was first Install, Otherwise (if user used option to backup), refers to previous snapshot 
 "snapshots": "[.snapshots]",
//Empty Value, if SBUILD didn't have it 
 "tag": "[.tag]"
}
</code></pre>
