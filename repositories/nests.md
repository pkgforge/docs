---
description: Self Hosted Mini Repositories for Soar
icon: kite
---

# Nests

{% hint style="info" %}
* [x] <mark style="color:purple;">**Nests**</mark> are <mark style="color:orange;">**self hosted**</mark> repositories that build & release packages on their own Account/Org/Repository/Registry. Think of them as [homebrew's tap](https://docs.brew.sh/Taps), but easier & better.
* [x] For <mark style="color:blue;">**Developers**</mark>, Nests are an easy way to distribute their applications easily & seamlessly to the target system or any \*Unix based distro
* [x] For <mark style="color:blue;">**Users**</mark>, Nests are an easy (& quicker) way to get their favourite applications as soon as new releases are made without waiting for any package manager (including us) to package it first.
{% endhint %}

***

## Developers

### Workflow

{% hint style="info" %}
* This will publish (mirror) your release on [**ghcr**](https://docs.github.com/en/packages/learn-github-packages/introduction-to-github-packages) & add a new **release** tag <mark style="color:green;">**`soar-nest`**</mark> to your repository
* The <mark style="color:green;">**`soar-nest`**</mark> release tag contains **JSON** metadata which soar uses to start ingesting your repository as a Nest.
{% endhint %}

1. Write and add an [<mark style="color:purple;">**`.SBUILD`**</mark>](broken-reference) to your Project. You can [**ask us**](https://discord.gg/djJUs48Zbu) for help.
2. Add something like this to your release pipeline or as another workflow

{% code overflow="wrap" %}
```yaml
name: 🧰🛠️ Build Soar Package 📦📀

##Optional:
# Setup minisign & add the private key as secret: MINISIGN_KEY [${{ secrets.MINISIGN_KEY }}]
# Setup a Read-Only Underprivileged Github Token as secret: RO_GHTOKEN [${{ secrets.RO_GHTOKEN }}]
# Setup a Read-Only Underprivileged GitLab Token as secret: RO_GLTOKEN [${{ secrets.RO_GLTOKEN }}]

#These permissions are needed by main CI
permissions:
  attestations: write #Needed for Build Provenance & Attestations
  contents: write #Needed to create Release
  id-token: write #Needed for Build Provenance & Attestations
  packages: write #Needed to push to ghcr

#Assuming you just published a new release & the SBUILD doesn't build from source                 
on:
  #push:
  workflow_dispatch:
  release:
    types: [published]

jobs:

#Assuming you are targeting a stable release
  stable-release:
    uses: pkgforge/soarpkgs/.github/workflows/matrix_builds.yaml@main
    with:
      host: "ALL" #Otherwise aarch64-Linux OR x86_64-Linux
      sbuild-url: "https://github.com/${{ github.repository }}/raw/main/.github/SBUILD/latest.yaml" #Must always be a raw URL
      ghcr-url: "ghcr.io/${{ github.repository }}/stable" #Package will be pushed under this path
      pkg-family: "YOUR-PKG-PRIMARY-NAME" #Needed so soar can cross reference with other repos/nests
      debug: false #If set to true, will run everything with set -x
      logs: true #Will Attach the entire Logs + File as Workflow Artifact
      rebuild: true #Will rebuild even if ghcr tag already exists
```
{% endcode %}

3. Check for the <mark style="color:green;">**`soar-nest`**</mark> release tag (It is marked as a <mark style="color:blue;">**Pre-Release**</mark>)
4. Update your <mark style="color:blue;">**README**</mark> to include a one-liner

```bash
soar nest add nestname github:owner/repo
```

* When performing operations, the **nest name** must be **prepended with `nest-`**.
  For example:

  ```bash
  soar ls nest-nestname
  ```
* Instead of adding a GitHub repo, users may also directly provide a link to a **compatible SQLite database** or a **JSON metadata file**.
  Example:

  ```bash
  soar nest add mynest https://example.com/metadata.json.zstd
  soar nest add mynest https://example.com/packages.db
  ```

{% hint style="warning" %}
* All values must be **lowercase** : [https://github.com/oras-project/oras/discussions/930](https://github.com/oras-project/oras/discussions/930) , the workflow will forcefully change all values to match this.
{% endhint %}

***

### Branding

{% hint style="warning" %}
* There's hardcoded stuff related to pkgforge, like filepath & some links.&#x20;
* The filename/paths should be harmless and are present only in CI, not the final artifact
* However the api-urls, can't be removed as it is needed & used by soar-core. Fallbacks are automatically used in case our api-urls ever die, so this is also harmless.
* Finally, there's some branding in the logfile, To disable banners in logfiles, set <mark style="color:blue;">**`banner:`**</mark><mark style="color:red;">**`false`**</mark>
{% endhint %}

***

### Security

{% hint style="danger" %}
By default, if you use our official workflows, you are pulling in code from our repos & then executing them on your repo with some over privileged perms. This is fine if you trust us not to do anything bad.

However, if you want to be extra careful, these mitagtions will help reduce any potential impact in case of incidents:

1. Always use the workflow on github actions with [github''s own JIT](https://docs.github.com/en/actions/security-for-github-actions/security-guides/automatic-token-authentication), so they would be generated & expired automatically.
2. Additionally, rather than using **pkgforge/soarpkgs/.github/workflows/matrix\_builds.yaml**<mark style="color:blue;">**@main**</mark> , audit our code, and then hardcode it to a particular commit hash **pkgforge/soarpkgs/.github/workflows/matrix\_builds.yaml@**<mark style="color:purple;">**${SHA}**</mark>
3. Additionally, separate your project's official project repo and soar's nest repo into two different repositories, so the token would have access to only soar's nest repo, not to your whole project
4. Additionally, read our code, and then rewrite it by yourself, on your own repo & run it on your own infra
{% endhint %}

***

### Quirks

{% hint style="warning" %}
* Nests won't **work on forked repos** because github needs it to be a real (detached) repository in order to push packages associated with that repo to ghcr.
* **Setup time** for a build job can be as **high as 10 minutes**, this is because the runner needs to be able to handle any & all scenarios. This is intentional, as developers can use any build tool or even docker/podman without having to specify install deps in the SBUILD itself. However, if the sbuild **only needs curl/wget**, the runner **will still go through the whole setup phase**. Currently there's no solution for this problem, we thank you for your understanding & welcome any ideas over at: [**soarpkgs/discussions**](https://github.com/pkgforge/soarpkgs/discussions)
{% endhint %}

***

## Users



