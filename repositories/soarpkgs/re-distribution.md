---
description: >-
  Documentation for re-distribution of our packages by third party package
  managers
icon: chart-network
---

# Re:Distribution

Any third-party package manager (i.e. not under our [PkgForge Org](https://docs.pkgforge.dev/orgs/readme/about) Umbrella), must follow these guidelines when re-distributing them. Hence forth, referred to as `third-parties`

{% hint style="success" %}
These don't apply if re-distributing is done only for personal use i.e not advertised as a package manager & instead they are being used in dotfiles or similar.
{% endhint %}

***

### Attribution

Any third-parties, must have a dedicated section on the main README of their project where the following things are made explicitly clear:

* [x] Any [Official Repositories](https://docs.pkgforge.dev/repositories) from Package Forge, must be marked as external & third party i.e. not your default repos & your users must know the actual source.&#x20;
* [x] Any [External/Third-Party](https://docs.pkgforge.dev/repositories/external) Repositories from Package Forge, must be marked as external & third party, same as Official Repositories from Package Forge, because for a third-party, all these are also external.&#x20;
* [x] The total percentage of packages used from our repos, compared to the third-parties' repos (if they have it) must be clearly specified.
* [x] Any data that's used from [pkgforge/metadata](https://github.com/pkgforge/metadata/) must be disclosed, especially if a third-party edits/re-edits it to match their own needs.

***

### Mandatory Fields

Any third-parties, must clearly show the following fields (from our metadata) to their user when installing any packages or querying information on any packages that come from our repositories (Official/External). These can be skipped if & only if these are missing (For instance, from our External Repositories).

* [x] Homepage: The `homepage` entry must show the Homepage URL(s) for the package & is our way of offering attribution/credits to the original Author(s) of the package.
* [x] Licenses: The `license` entry must show the SPDX Identifier of the package & is a legal requirement.
* [x] Maintainers: The `maintainer` entry must show the Recipe (SBUILD) maintainer(s) of the package & is our way of both offering attribution/credits to the maintainer(s) & and transfer responsibility.
* [x] Notes: The `note` entry must show the Note(s) associated with a Package. This often contains crucial information we want the User to be aware of about the package.
* [x] Sources: The `src_url` entry must show the Source URL(s) for the Package & it's purpose is similar to displaying Homepage.
* [x] Index: The `pkg_webpage` entry must show the URL to our online Index, which contains all the fields for the package & serves as a way for users to know everything even when a third-party has decided to exclude most of those fields.

#### Examples:

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption><p>Notes displayed by default when Installing a Package</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption><p>Query/Info on a Package</p></figcaption></figure>

***

### Mandatory Files

Any third-parties, must also re-distribute the following files in addition to the main binary for the Package. An option can be offered to users to exclude this, but by default, the third party can't make this decision for the users, & thus must comply.

* [x] LICENSE: For legal reasons, the `LICENSE` file must be downloaded & installed in the user's system.

#### Examples:

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption><p>License downloaded/copied/installed by default</p></figcaption></figure>

***

