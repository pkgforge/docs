---
icon: gear
description: List of Environment Variables that are Accessible Inside x_exec.run
---

# ENV\_VARS (x\_exec.run)

{% hint style="danger" %}
<mark style="color:orange;">**Anything else that's NOT Listed**</mark>**&#x20;here,&#x20;**<mark style="color:red;">**should NOT be Accessible**</mark>**&#x20;Inside&#x20;**<mark style="color:purple;">**x\_exec.run**</mark>**&#x20;context**
{% endhint %}

* [x] <mark style="color:orange;">**`${pkg}`**</mark>**&#x20;|&#x20;**<mark style="color:orange;">**`{PKG}`**</mark>

> - **Description**: The raw value of [<mark style="color:purple;">**`.pkg`**</mark>](../specification/2.pkg.md) from <mark style="color:purple;">**`.SBUILD`**</mark> <<mark style="color:green;">**ALWAYS**</mark> _Available_>

* [x] <mark style="color:orange;">**`${pkg_id}`**</mark> | <mark style="color:orange;">**`${PKG_ID}`**</mark>

> - **Description**: The raw value of [<mark style="color:purple;">**`.pkg_id`**</mark>](../specification/2.pkg.md) from <mark style="color:purple;">**`.SBUILD`**</mark> <<mark style="color:red;">**Empty**</mark> _if not Available_>

* [x] <mark style="color:orange;">**`${pkg_type}`**</mark> | <mark style="color:orange;">**`${PKG_TYPE}`**</mark>

> - **Description**: The raw value of [<mark style="color:purple;">**`.pkg_type`**</mark>](../specification/2.pkg.md) from <mark style="color:purple;">**`.SBUILD`**</mark> <<mark style="color:red;">**Empty**</mark> _if not Available_>

* [x] <mark style="color:orange;">**`${pkg_ver}`**</mark> | <mark style="color:orange;">**`${PKG_VER}`**</mark>

> - **Description**: The raw value of [<mark style="color:purple;">**`.pkgver`**</mark>](../specification/3.version.md) **OR** the output produced by [<mark style="color:purple;">**`x_exec.pkgver`**</mark>](../specification/20.x_exec.md)from<mark style="color:purple;">**`.SBUILD`**</mark> <<mark style="color:green;">**ALWAYS**</mark> _Available_>
> - &#x20;This is the same as the raw content of <mark style="color:orange;">**${SBUILD\_PKG}.version**</mark> file

* [x] <mark style="color:orange;">**`${SBUILD_PKG}`**</mark>

> - **Description**: The raw value of [<mark style="color:purple;">**`.pkg`**</mark>](../specification/2.pkg.md) + [<mark style="color:purple;">**.pkg\_type**</mark>](../specification/2.pkg.md) from <mark style="color:purple;">**`.SBUILD`**</mark> <<mark style="color:green;">**ALWAYS**</mark> _Available_>
> - **ALWAYS USE** <mark style="color:orange;">**${SBUILD\_PKG}**</mark> for **output**, example: <mark style="color:orange;">**${SBUILD\_PKG}**</mark> (<mark style="color:blue;">**Main Binary**</mark>), <mark style="color:orange;">**${SBUILD\_PKG}.png**</mark> (<mark style="color:blue;">**Icon**</mark>), <mark style="color:orange;">**${SBUILD\_PKG}.desktop**</mark> (<mark style="color:blue;">**Desktop**</mark>) etc

* [x] <mark style="color:orange;">**`${SBUILD_OUTDIR}`**</mark>

> - **Description**: The **Root** (<mark style="color:orange;">**Temporary**</mark>) <mark style="color:blue;">**Working Directory**</mark> [<mark style="color:purple;">**`x_exec.run`**</mark>](../specification/20.x_exec.md) is Run From <<mark style="color:green;">**ALWAYS**</mark> _Available_>
> - **All** [**NEEDED Files**](needed_files.md) **must exist in this&#x20;**<mark style="color:orange;">**Directory**</mark>

* [x] <mark style="color:orange;">**`${SBUILD_TMPDIR}`**</mark>

> - **Description**: The <mark style="color:purple;">**SBUILD\_TEMP**</mark> <mark style="color:blue;">**Directory**</mark> inside <mark style="color:orange;">**${SBUILD\_OUTDIR}**</mark> (**PATH**: <mark style="color:orange;">**`${SBUILD_OUTDIR}/`**</mark><mark style="color:purple;">**`SBUILD_TEMP`**</mark>), used for storing _NON-NEEDED_ Files <<mark style="color:green;">**ALWAYS**</mark> _Available_>
> - Use this dir to do Additional Steps, **keep the main&#x20;**<mark style="color:orange;">**${SBUILD\_OUTDIR}**</mark>**&#x20;clutter free**

* [x] <mark style="color:orange;">**`${USER_AGENT}`**</mark>

> - **Description**: <mark style="color:blue;">**User-Agent**</mark> from **Host** <<mark style="color:red;">**Empty**</mark> _if not Available_>
> - If available & inherited, the <mark style="color:orange;">**Runner**</mark> will use it as the User Agent Header for all **HTTP** Requests.
> - &#x20;If used <mark style="color:orange;">`--no-hostenv`</mark>, then this <mark style="color:purple;">**ENV\_VAR**</mark> is **NOT TO BE INHERITED/INSERTED AT ALL**

* [x] [<mark style="color:orange;">**`${GITHUB_TOKEN}`**</mark>](https://cli.github.com/) | [<mark style="color:orange;">**`${GH_TOKEN}`**</mark>](https://cli.github.com/)

> - **Description**: <mark style="color:blue;">**Github Token**</mark> from **Host** <<mark style="color:red;">**Empty**</mark> _if not Available_>
> - If available & inherited, the <mark style="color:orange;">**Runner**</mark> will use it as the Token to make **Github API** Requests.
> - &#x20;If used <mark style="color:orange;">`--no-hostenv`</mark>, then this <mark style="color:purple;">**ENV\_VAR**</mark> is **NOT TO BE INHERITED/INSERTED AT ALL**

* [x] [<mark style="color:orange;">**`${GITLAB_TOKEN}`**</mark>](https://gitlab.com/gitlab-org/cli) | [<mark style="color:orange;">**`${GL_TOKEN}`**</mark>](https://gitlab.com/gitlab-org/cli)

> - **Description**: <mark style="color:blue;">**Gitlab Token**</mark> from **Host** <<mark style="color:red;">**Empty**</mark> _if not Available_>
> - If available & inherited, the <mark style="color:orange;">**Runner**</mark> will use it as the Token to make **Gitlab API** Requests.
> - &#x20;If used <mark style="color:orange;">`--no-hostenv`</mark>, then this <mark style="color:purple;">**ENV\_VAR**</mark> is **NOT TO BE INHERITED/INSERTED AT ALL**

* [x] [<mark style="color:orange;">**`${HF_TOKEN}`**</mark>](https://huggingface.co/docs/huggingface_hub/en/guides/cli)

> - **Description**: <mark style="color:blue;">**HuggingFaceHub Token**</mark> from **Host** <<mark style="color:red;">**Empty**</mark> _if not Available_>
> - If available & inherited, the <mark style="color:orange;">**Runner**</mark> will use it as the Token to make **HF API** Requests.
> - &#x20;If used <mark style="color:orange;">`--no-hostenv`</mark>, then this <mark style="color:purple;">**ENV\_VAR**</mark> is **NOT TO BE INHERITED/INSERTED AT ALL**

***

* [x] <mark style="color:blue;">**MISC**</mark>

{% hint style="info" %}
If <mark style="color:orange;">**`--no-hostenv`**</mark>is used, the <mark style="color:purple;">**`ENV VARS`**</mark> below are to be created from scratch based on the fallback that's described for each.
{% endhint %}

> * [x] <mark style="color:green;">**LANG**</mark>: The Locale Setting, If this is empty/non-existent (or used <mark style="color:orange;">`--no-hostenv`</mark>) , Use <mark style="color:orange;">**`C.UTF-8`**</mark>(<mark style="color:green;">**`LANG`**</mark>**`=`**<mark style="color:orange;">**`C.UTF-8`**</mark>)
> * [x] <mark style="color:green;">**LC\_ALL**</mark>: The Locale Setting, If this is empty/non-existent (or used <mark style="color:orange;">`--no-hostenv`</mark>) , Use <mark style="color:orange;">**`C.UTF-8`**</mark>(<mark style="color:green;">**`LC_ALL`**</mark>**`=`**<mark style="color:orange;">**`C.UTF-8`**</mark>)
> * [x] <mark style="color:green;">**PATH**</mark>: The <mark style="color:orange;">**`${PATH}`**</mark> from <mark style="color:blue;">**HOST**</mark>, if this is empty/non-existent (or used <mark style="color:orange;">`--no-hostenv`</mark>), Use: <mark style="color:orange;">**`${SOAR_BINPATH}:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin`**</mark>(Example: <mark style="color:green;">**`PATH`**</mark>**`=`**<mark style="color:orange;">**`/home/example/.local/share/soar/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin`**</mark>)
> * [x] <mark style="color:green;">**PWD**</mark>: The Present Working Directory, this should be set to the **full realpath of** <mark style="color:orange;">**`${SBUILD_OUTDIR}`**</mark>, as the [<mark style="color:purple;">**`x_exec.run`**</mark>](../specification/20.x_exec.md) is run from this dir. <<mark style="color:green;">**ALWAYS**</mark> _Available_> (Example: <mark style="color:green;">**`PWD`**</mark>**`=`**<mark style="color:orange;">**`/home/example/.local/share/soar/cache/sbuild/github.com.example.example.stable`**</mark>)
> * [x] <mark style="color:green;">**SHELL**</mark>: The value of [<mark style="color:purple;">**`x_exec.shell`**</mark>](../specification/20.x_exec.md) **after resolving with env** so it prints **full realpath** of  [<mark style="color:purple;">**`x_exec.shell`**</mark>](../specification/20.x_exec.md) <<mark style="color:green;">**ALWAYS**</mark> _Available_> (<mark style="color:green;">**`SHELL`**</mark>**`=`**<mark style="color:orange;">**`/bin/bash`**</mark>)
> * [x] <mark style="color:green;">**TERM**</mark>: The terminal emulator, this is needed as some CLI progs behave unexpectedly without it. If this is empty/non-existent (or used <mark style="color:orange;">`--no-hostenv`</mark>), Use: <mark style="color:orange;">**`XTERM`**</mark> (<mark style="color:green;">**`TERM`**</mark>**`=`**<mark style="color:orange;">**`xterm`**</mark>)
> * [x] <mark style="color:green;">**USER**</mark>: The current **$USER** (<mark style="color:orange;">`whoami`</mark>) If this is empty/non-existent, it is to be determined & inserted manually. If used <mark style="color:orange;">`--no-hostenv`</mark>, then this <mark style="color:purple;">**ENV\_VAR**</mark> is **NOT TO BE INHERITED/INSERTED AT ALL**
