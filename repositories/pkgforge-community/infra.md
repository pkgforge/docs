---
icon: server
description: Build & CI Servers
---

# Infra

### Workflow

1. pkgforge-community only consists of [pkgforge/soarpkgs](https://github.com/pkgforge/soarpkgs) ([Repository](https://docs.pkgforge.dev/orgs/pkgforge-core/projects/soarpkgs)) &  [pkgforge-community](https://github.com/pkgforge-community) ([Org](https://docs.pkgforge.dev/orgs/pkgforge-community))
2. [pkgforge/soarpkgs](https://github.com/pkgforge/soarpkgs) ([Repository](https://docs.pkgforge.dev/orgs/pkgforge-core/projects/soarpkgs)) contains [<mark style="color:purple;">**`SBUILD`**</mark>](broken-reference) [**Recipes**](https://github.com/pkgforge/soarpkgs/tree/main/packages), these are just scripts that are run on the user's own system.
3. [pkgforge-community](https://github.com/pkgforge-community) ([Org](https://docs.pkgforge.dev/orgs/pkgforge-community)) maintains forks of <mark style="color:red;">**Unofficial**</mark> Packages, you can read why: [https://github.com/pkgforge-community#why-did-you-fork-my-repo](https://github.com/pkgforge-community#why-did-you-fork-my-repo), these runs on [GitHub's Free Workflow Runners](https://docs.github.com/en/actions/using-github-hosted-runners/using-github-hosted-runners)

### Cost

{% hint style="info" %}
1. All the projects listed above require no dedicated infra, as such there's no monetary cost involved.&#x20;
2. There's still some overlap in the Infra with [pkgforge-edge/infra](https://docs.pkgforge.dev/repositories/pkgforge-edge/infra) & [pkgforge-stable/infra](https://docs.pkgforge.dev/repositories/pkgforge-stable/infra), particularly [CloudFlare workers](https://developers.cloudflare.com/workers/platform/pricing/) for the domains & Our [Reverse Proxies to GitHub](https://github.com/pkgforge-dev/reverse-proxies) etc, but this cost is covered by the other repositories.
3. We extend our gratitude to all the contributors who have generously dedicated their personal free time and continue to do so
{% endhint %}
