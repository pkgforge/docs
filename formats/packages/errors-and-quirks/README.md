---
icon: triangle-exclamation
description: Common issues with portable packages
---

# Errors & Quirks

Things a portable package can still want from the host, and what to do when it is missing:

* [**FUSE**](fuse.md): how a package mounts its own payload. Only some runtimes need it installed.
* [**Fonts**](fonts.md): required to render non-English characters, symbols and emoji.
* [**Kernel user namespaces**](namespaces.md): used for sandboxing, and as a fallback when FUSE is unavailable.
