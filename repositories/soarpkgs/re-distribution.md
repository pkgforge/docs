---
description: >-
  Documentation for re-distribution of our packages by third party package
  managers
icon: chart-network
---

# Re:Distribution

Any third-party package manager (i.e. not under our [PkgForge Org](https://docs.pkgforge.dev/orgs/readme/about) Umbrella), must follow these guidelines when re-distributing them. Hence forth, referred to as `third-parties` .&#x20;

{% hint style="danger" %}
Failure to comply will force our hands to no longer make the metadata (& other files these third-parties depend on) available. As well as blacklisting these clients from using our apis & other services.&#x20;
{% endhint %}

{% hint style="success" %}
**Personal Use Exception**: These guidelines don't apply to personal redistribution (dotfiles, private scripts, etc.) that isn't advertised as a public package manager service.
{% endhint %}

***

### Attribution

Any third-parties, must have a dedicated section on the main README of their project where the following things are made explicitly clear:

* [x] Any [Official Repositories](https://docs.pkgforge.dev/repositories) from Package Forge, must be marked as external & third party i.e. not your default repos & your users must know the actual source.&#x20;
* [x] Any [External/Third-Party](https://docs.pkgforge.dev/repositories/external) Repositories from Package Forge, must be marked as external & third party, same as Official Repositories from Package Forge, because for a third-party, all these are also external.&#x20;
* [x] Specify the percentage of packages sourced from PkgForge repositories versus your own repositories
* [x] Any data that's used from [pkgforge/metadata](https://github.com/pkgforge/metadata/) must be disclosed, especially if a third-party edits/re-edits it to match their own needs.
* [x] Issue Tracker link for reporting issues with Packages that originate from PkgForge

#### Examples:

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption><p>Proper &#x26; Explicit Attribution with Links</p></figcaption></figure>

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

Any third-parties, must also re-distribute the following files in addition to the main binary for the Package. An option can be offered to users to exclude this, but by default, the third party can't make this decision for the users, & thus must comply. Users may opt-out, but this must be their explicit choice, not your default behavior.

{% hint style="success" %}
These don't apply if a third-party is a simply a downloader & not an installer i.e if a third party has a sub command to only download a package but not install it, then these files can be skipped.
{% endhint %}

* [x] LICENSE: For legal reasons, the `LICENSE` file must be downloaded & installed in the user's system.

#### Examples:

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption><p>License downloaded/copied/installed by default</p></figcaption></figure>

***

### Media

Any third-parties, when posting about their project anywhere through blogs, posts, comments or similar must follow these guidelines:

* [x] The third-party must not claim any additions/announcements/deletions/features/ports originating from our Packages/Projects/Repos as their own, unless the third party also directly contributed to it. We, PkgForge reserve the sole rights to publishing these at our own discretion.
* [x] The third-party must not advertise Package counts without disclosing the source as their own, unless the majority of the packages are from the third-party's own official repo & not ours (Official/External).
* [x] The third-party must not advertise itself as "official" as the only "official" projects are all under our PkgForge Org.

#### Examples:

<div align="left"><figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption><p>Misleading Claim with no Source</p></figcaption></figure> <figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption><p>Package Count with explicit Source</p></figcaption></figure></div>

Bad press release (without our Permission):

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption><p>Press Release, but self-credited (with 0 contributions)</p></figcaption></figure>

Good Press Release

```markdown
## Package Repository
- 15,000+ packages available
- Source: 12,000 from PkgForge repositories, 3,000+ maintained locally

## Recent Updates
- New packages added to PkgForge collection
- Read the official announcement: [PkgForge Blog](...)
```

**Avoid:**

* "We've added 50 new packages!" (when they're from PkgForge)
* "Official package manager for..." (without authorization)
* Press releases about PkgForge features without permission

***

### Compliance and Support

For questions about these guidelines or to request clarification, [contact us through our official channels](https://docs.pkgforge.dev/contact/chat). We're committed to working with third-party distributors who respect these requirements and help maintain the integrity of the PkgForge ecosystem.

These guidelines ensure proper attribution, legal compliance, and clear communication about package sources while supporting the broader package management community.
