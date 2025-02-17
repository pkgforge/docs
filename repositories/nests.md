---
icon: kite
description: Self Hosted Mini Repositories for Soar
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
soar nest add "https://github.com/YOUR-USERNAME/YOUR-ORG"
```

***

## Users



