---
icon: box-open
description: Binary types
---

# Binaries

A package that is one executable file, with nothing to mount or extract.

* [Static](static/), statically linked and needing no libc on the host

Dynamically linked binaries are not published. They are not portable across distributions, which is the property this whole project rests on, so a program that cannot be built statically is shipped as a self-contained [package format](../packages/) instead.
