---
icon: shield-quartered
description: Security
---

# Security

The format is the first line of defence. Nothing in soarpkgs executes, so there is no build script to review for what it does at run time. What a package is amounts to a URL, a hash and a list of paths, all of them visible in the diff.

* Every artifact is pinned by its blake3 hash, in git. Changing what a package downloads means changing a line somebody has to approve.
* Every package states its upstream, through `[update] repo` or `[pkg] src`, so provenance is always visible.
* The published index is signed with minisign. The public key lives in [keys/](https://github.com/pkgforge/soarpkgs/blob/main/keys/minisign.pub) and is shipped with Soar.
* Signature and hash are checked independently, so a validly signed index carrying a wrong hash still fails at install.
* Anyone can verify a package without trusting this repository: download the pinned URL, hash it, compare against the version file.
* Packages that cannot be pinned from an upstream release are built in [pkgforge/builds](../../packaging/builds.md), which pins its sources by commit and its toolchain by image digest, and rebuilds published packages on a schedule to check they still reproduce.

## Reporting

Report a vulnerability through [SECURITY.md](https://github.com/pkgforge/soarpkgs/blob/main/SECURITY.md), or privately through [chat](../../contact/chat.md) if public disclosure would make things worse. High and critical issues are addressed within 24 hours of being reported.
