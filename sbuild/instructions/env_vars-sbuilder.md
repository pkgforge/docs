---
icon: gear
description: Environment Variables for SBUILDER
---

# ENV\_VARS (SBUILDER)

{% hint style="info" %}
This is internal documentation meant for the **`SBUILDER`**, **not for humans** [writing SBUILD Scripts](broken-reference)
{% endhint %}

* [x] <mark style="color:orange;">**`${SBUILD_SUCCESSFUL}`**</mark>

> - **Description**: If the <mark style="color:blue;">**Build**</mark> Was <mark style="color:green;">**Successful**</mark> or <mark style="color:red;">**Failed**</mark>, if It <mark style="color:red;">**Failed**</mark> (<mark style="color:orange;">**`SBUILD_SUCCESSFUL`**</mark>**`==`**<mark style="color:red;">**`false`**</mark>) **Bail & Exit Immediately (Still Copy&#x20;**<mark style="color:orange;">**`${SBUILD_OUTDIR}`**</mark>**&#x20;to&#x20;**<mark style="color:orange;">**`SOAR_CACHE`**</mark>**) (**
> - **Also Copy&#x20;**<mark style="color:orange;">**`${SBUILD_TMPDIR}`**</mark>(**PATH**: <mark style="color:orange;">**`${SBUILD_OUTDIR}/`**</mark><mark style="color:purple;">**`SBUILD_TEMP`**</mark>) if **used** <mark style="color:orange;">**`-k | --keep`**</mark>
> - **Values**: <mark style="color:green;">**`true`**</mark> | <mark style="color:red;">**`false`**</mark>

* [x] <mark style="color:orange;">**`${PKG}`**</mark>

> - **Description**: The <mark style="color:blue;">**Package Name**</mark>, used as <mark style="color:blue;">**Prefix**</mark> for [**ALL NEEDED Files**](needed_files.md) <<mark style="color:green;">**ALWAYS**</mark> Available>
> - **Value**: [<mark style="color:purple;">**`.pkg`**</mark>](../specification/2.pkg.md)

* [x] <mark style="color:orange;">**`${PKG_ID}`**</mark>

> - **Description**: The <mark style="color:blue;">**Package ID**</mark> (value: [<mark style="color:purple;">**`.pkg_id`**</mark>](../specification/2.pkg.md))
> - Also used as **default&#x20;**<mark style="color:blue;">**OutputDir**</mark>**&#x20;if** <mark style="color:orange;">**`-o | --output`**</mark><mark style="color:blue;">**`PATH`**</mark> was **NOT Specified** (**ONLY IF** <mark style="color:orange;">**`SBUILD_SUCCESSFUL`**</mark>**`==`**<mark style="color:green;">**`true`**</mark>)

* [x] <mark style="color:orange;">**`${SBUILD_PKG}`**</mark>

> - **Description**: The <mark style="color:blue;">**Package Name**</mark> + <mark style="color:blue;">**Package ID**</mark>
> - **Value**: [<mark style="color:purple;">**`.pkg`**</mark>](../specification/2.pkg.md)[<mark style="color:purple;">**`+ .pkg_type`**</mark>](../specification/2.pkg.md)

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
