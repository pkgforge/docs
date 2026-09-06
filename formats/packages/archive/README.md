---
description: >-
  Extract-and-run archives, usually published by upstream itself.
icon: box-taped
---

# Archive

A plain compressed archive, extracted into the package directory rather than run as a single file. The [recipe](../../../packaging/recipe.md) says what to take out of it and where each file lands, so a tarball carrying a binary, a manual page and shell completions ends up integrated the same way a native package would be.

{% hint style="success" %}
<mark style="color:purple;">**Sources**</mark>

* Upstream's own release archive, wherever it publishes a portable one
* A registry like [npm](https://www.npmjs.com/) or [PyPI](https://pypi.org/) when upstream publishes no binary at all
{% endhint %}

{% hint style="info" %}
An archive is a container rather than a format in its own right, so a package's `type` usually names what comes out of it. A tarball holding a static binary is a `static` package whose recipe installs paths out of the archive. See [`[source.install]`](../../../packaging/recipe.md).
{% endhint %}

An archive that is not portable as published has to be made portable before it can be shipped, with [sharun](https://github.com/VHSgunzo/sharun), [wrappe](https://github.com/Systemcluster/wrappe) or [onelf](../onelf/). That is a build, so it happens in [pkgforge/builds](../../../packaging/builds.md) rather than in a recipe.
