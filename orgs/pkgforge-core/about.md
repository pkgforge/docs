---
icon: circle-info
---

# About

{% embed url="https://soar.pkgforge.dev/gif?tmp.T8cejqbouL=tmp.zCz9xm0XHw" %}

[PkgForge](https://github.com/pkgforge) provides portable packages and static binaries for Linux, and builds [Soar](../../soar/readme/), the package manager that installs them.

The two are deliberately separate. Soar reads a metadata index and installs what it finds; it does not build or host anything. [soarpkgs](../../repositories/soarpkgs/) produces that index from a tree of declarative package definitions. Either side can be replaced without the other, which is why [running your own repository](../../repositories/external/) is a supported thing to do rather than a fork.

* [PkgForge-Dev](../pkgforge-dev/), development and experimental projects
* [History](history.md), how the project got here
