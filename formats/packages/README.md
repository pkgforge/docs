---
icon: compact-disc
description: Portable package formats
---

# Packages

Self-contained formats that carry an application and everything it needs, so it runs on any Linux distribution without being installed into one.

* [AppImage](appimage/), single-file portable applications
* [onelf](onelf/), directories packed into self-contained executables
* [AppBundle](appbundle/), portable app bundles
* [FlatImage](flatimage/), Flatpak-style sandboxing with AppImage portability
* [RunImage](runimage/), single-file containers
* [NixAppImage](nixappimage/), AppImages built from Nix derivations
* [Archive](archive/), extract and run

Soar handles all of them, and a [recipe](../../packaging/recipe.md) can name any of them as its `type`. Which ones you actually find in [soarpkgs](../../repositories/soarpkgs/) is a question about what upstreams publish rather than about the format: `static` and `appimage` cover nearly everything today, with a couple of `onelf` packages.

## Troubleshooting

See [Errors & Quirks](errors-and-quirks/) for the host-side requirements these formats share: FUSE, fonts, and kernel user namespaces.
