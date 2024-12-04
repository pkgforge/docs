---
icon: not-equal
description: Differences from bincache/pkgcache
---

# Differences

| [**`SoarPkgs`**](https://github.com/pkgforge/soarpkgs)                                                                                                      | [**`BinCache`**](https://github.com/Azathothas/Toolpacks)/[**`PkgCache`**](https://github.com/pkgforge/pkgcache)                                                |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **No PreBuilt Cache**, All Packages are Built & Installed Locally                                                                                           | **`PreBuilt`** [**Binary Cache**](broken-reference)/[**Package Cache**](broken-reference), All Packages are Downloaded & Installed Directly from Remote Sources |
| [<mark style="color:purple;">**`.SBUILD`**</mark>](broken-reference) runs Locally on User's System, so Security depends on each package & their Maintainers | All Scripts are run on **Secure Isolated Containers** & Transparent Build Logs are provided, but Security still depends on each Package                         |
| No Restrictions of Addition/Acceptance of Packages                                                                                                          | **Only Truly Portable Packages** are accepted, i.e. all packages added must run on **`GLIBC/MUSL`** & Require no additional dependencies                        |
| **Decentralized**                                                                                                                                           | **Centralized** & Managed by [**PkgForge's Core Team**](../../people.md)                                                                                        |
| Local Resources like CPU, MEM, DISK, Bandwidth etc Are Used                                                                                                 | Only Storage (Disk) & Bandwidth is Used                                                                                                                         |
| Contribution GuideLine is Simple & Forgiving                                                                                                                | Each Contribution goes through Rigorous Review before being Merged                                                                                              |
