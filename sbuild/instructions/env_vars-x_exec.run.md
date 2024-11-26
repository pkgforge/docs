---
icon: gear
description: List of Environment Variables that are Accessible Inside x_exec.run
---

# ENV\_VARS (x\_exec.run)

* [x] <mark style="color:orange;">**`${pkg}`**</mark>**&#x20;|&#x20;**<mark style="color:orange;">**`{PKG}`**</mark>

> - **Description**: The raw value of [<mark style="color:purple;">**`.pkg`**</mark>](../specification/2.pkg.md) from <mark style="color:purple;">**`.SBUILD`**</mark> <<mark style="color:green;">**ALWAYS**</mark> _Available_>

* [x] <mark style="color:orange;">**`${pkg_id}`**</mark> | <mark style="color:orange;">**`${PKG_ID}`**</mark>

> - **Description**: The raw value of [<mark style="color:purple;">**`.pkg_id`**</mark>](../specification/2.pkg.md) from <mark style="color:purple;">**`.SBUILD`**</mark> <<mark style="color:red;">**Empty**</mark> _if not Available_>

* [x] <mark style="color:orange;">**`${pkg_type}`**</mark> | <mark style="color:orange;">**`${PKG_TYPE}`**</mark>

> - **Description**: The raw value of [<mark style="color:purple;">**`.pkg_type`**</mark>](../specification/2.pkg.md) from <mark style="color:purple;">**`.SBUILD`**</mark> <<mark style="color:red;">**Empty**</mark> _if not Available_>

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

* [x] [<mark style="color:orange;">**`${GITHUB_TOKEN}`**</mark>](https://cli.github.com/) | [<mark style="color:orange;">**`${GH_TOKEN}`**</mark>](https://cli.github.com/)

> - **Description**: <mark style="color:blue;">**Github Token**</mark> from **Host** <<mark style="color:red;">**Empty**</mark> _if not Available_>
> - If available & inherited, the <mark style="color:orange;">**Runner**</mark> will use it as the Token to make **Github API** Requests.

* [x] [<mark style="color:orange;">**`${GITLAB_TOKEN}`**</mark>](https://gitlab.com/gitlab-org/cli) | [<mark style="color:orange;">**`${GL_TOKEN}`**</mark>](https://gitlab.com/gitlab-org/cli)

> - **Description**: <mark style="color:blue;">**Gitlab Token**</mark> from **Host** <<mark style="color:red;">**Empty**</mark> _if not Available_>
> - If available & inherited, the <mark style="color:orange;">**Runner**</mark> will use it as the Token to make **Gitlab API** Requests.

* [x] [<mark style="color:orange;">**`${HF_TOKEN}`**</mark>](https://huggingface.co/docs/huggingface_hub/en/guides/cli)

> - **Description**: <mark style="color:blue;">**HuggingFaceHub Token**</mark> from **Host** <<mark style="color:red;">**Empty**</mark> _if not Available_>
> - If available & inherited, the <mark style="color:orange;">**Runner**</mark> will use it as the Token to make **HF API** Requests.
