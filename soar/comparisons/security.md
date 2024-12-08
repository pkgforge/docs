---
icon: lock
description: Security Postures
---

# 4. Security

{% hint style="info" %}
**Before proceeding, we&#x20;**<mark style="color:green;">**recommend**</mark>**&#x20;reading**:&#x20;

* [x] [https://docs.pkgforge.dev/repositories/pkgforge-edge/security](https://docs.pkgforge.dev/repositories/pkgforge-edge/security)
* [x] [https://docs.pkgforge.dev/repositories/pkgforge-community/security](https://docs.pkgforge.dev/repositories/pkgforge-community/security)
{% endhint %}

***

### Build/Install

| Package Manager                                              | Privileged?                                                              | Sandbox?                                                            | Validation?                                                                                                                                                                                                                                                       | Log?                                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| [**`AM`**](https://github.com/ivan-hc/AM/tree/main/programs) | [<mark style="color:orange;">**Depends**</mark>](#user-content-fn-1)[^1] | [<mark style="color:red;">**No**</mark>](#user-content-fn-2)[^2]    | [<mark style="color:red;">**None**</mark>](#user-content-fn-3)[^3]                                                                                                                                                                                                | <mark style="color:red;">**None**</mark>                                 |
| [**`Brew`**](https://brew.sh/)                               | [<mark style="color:green;">**No**</mark>](#user-content-fn-4)[^4]       | [<mark style="color:red;">**No**</mark>](#user-content-fn-5)[^5]    | [<mark style="color:green;">**Checksum**</mark>](#user-content-fn-6)[^6] + [**Artifact Attestations**](https://docs.github.com/en/actions/security-for-github-actions/using-artifact-attestations/using-artifact-attestations-to-establish-provenance-for-builds) | [<mark style="color:orange;">**Kind Of**</mark>](#user-content-fn-7)[^7] |
| [**`Pacstall`**](https://github.com/pacstall)                | [<mark style="color:red;">**Yes**</mark>](#user-content-fn-8)[^8]        | [<mark style="color:green;">**Yes**</mark>](#user-content-fn-9)[^9] | [<mark style="color:orange;">**Depends**</mark>](#user-content-fn-10)[^10]                                                                                                                                                                                        | [<mark style="color:orange;">**No\***</mark>](#user-content-fn-11)[^11]  |
| [**`PPKG`**](https://github.com/leleliu008/ppkg)             | [<mark style="color:green;">**No**</mark>](#user-content-fn-12)[^12]     | [<mark style="color:red;">**No**</mark>](#user-content-fn-13)[^13]  | [<mark style="color:green;">**Checksum**</mark>](#user-content-fn-14)[^14]                                                                                                                                                                                        | [<mark style="color:green;">**Yes**</mark>](#user-content-fn-15)[^15]    |
| [**`Soar`**](https://github.com/pkgforge/soar)               | [<mark style="color:green;">**No**</mark>](#user-content-fn-16)[^16]     | -                                                                   | [<mark style="color:green;">**Checksum**</mark>](#user-content-fn-17)[^17]                                                                                                                                                                                        | [<mark style="color:green;">**Yes**</mark>](#user-content-fn-18)[^18]    |



[^1]: <mark style="color:red;">**AM runs each script as sudo**</mark>\
    AppMan runs with user privilege

[^2]: AM runs each script with sudo privilege & unsandboxed.\
    AppMan doesn't need sudo, but still runs the script unsandboxed

[^3]: No validation of any sort

[^4]: They actively warn: [https://docs.brew.sh/FAQ#why-does-homebrew-say-sudo-is-bad](https://docs.brew.sh/FAQ#why-does-homebrew-say-sudo-is-bad)

[^5]: Their sandboxing is only for MacOS

[^6]: sha256sum

[^7]: You have to find the PR at their Github Page & then see the job output

[^8]: Needs during install. Sometimes even during build

[^9]: Yes, with bwrap: [https://github.com/pacstall/pacstall/blob/develop/misc/scripts/bwrap.sh](https://github.com/pacstall/pacstall/blob/develop/misc/scripts/bwrap.sh)

[^10]: Some pacscripts have it, some don't

[^11]: Only whatever is done locally

[^12]: Build is entirely unprivileged

[^13]: Builds happen with current user privs

[^14]: sha256sum

[^15]: Quite Verbose Logging since everything is built from source

[^16]: No doas/sudo, at any time for any reason

[^17]: b3sum + sha256sum

[^18]: Transparent CI + Local log: <mark style="color:orange;">`soar log $pkg`</mark>
