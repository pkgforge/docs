---
description: https://kokada.dev/blog/building-static-binaries-in-nix/
icon: snowflake
---

# Nix

### Native

{% code overflow="wrap" %}
```bash
#Create Dir for later
mkdir -pv "./OUTDIR"

#Build and Output to ./TMPDIR (Symlink)
NIXPKGS_ALLOW_BROKEN="1" NIXPKGS_ALLOW_UNSUPPORTED_SYSTEM="1" \
nix-build '<nixpkgs>' --attr "pkgsStatic.${PKG_NAME}" --impure \
--cores "$(($(nproc)+1))" --max-jobs "$(($(nproc)+1))" \
--log-format bar-with-logs --out-link "./TMPDIR"

#Copy (Dir may differ)
sudo rsync -av --copy-links "./TMPDIR/bin/." "./OUTDIR"
sudo chown -R "$(whoami):$(whoami)" "./OUTDIR" && chmod -R 755 "./OUTDIR"

#Strip & File
find "./OUTDIR" -type f -exec objcopy --remove-section=".comment" --remove-section=".note.*" "{}" \;
find "./OUTDIR" -type f ! -name "*.no_strip" -exec strip --strip-debug --strip-dwo --strip-unneeded --preserve-dates "{}" \;
find "./OUTDIR" -type f -print | xargs -I {} sh -c 'file {}; b3sum {}; sha256sum {}; du -sh {}'

#Cleanup
nix-collect-garbage >/dev/null 2>&1
```
{% endcode %}

### Cross

{% code overflow="wrap" %}
```bash
#Create Dir for later
mkdir -pv "./OUTDIR"

#${NIX_TARGET}: https://github.com/Azathothas/Toolpacks/blob/main/Docs/NIX_TARGETS.txt
nix-instantiate --eval --strict --expr 'let pkgs = import <nixpkgs> {}; pkgsCross = pkgs.pkgsCross; in builtins.attrNames pkgsCross' | tr -d '[]"' | tr ' ' '\n' | sed '/^\s*$/d'

#Build and Output to ./TMPDIR (Symlink)
NIXPKGS_ALLOW_BROKEN="1" NIXPKGS_ALLOW_UNSUPPORTED_SYSTEM="1" \
nix-build '<nixpkgs>' --attr "pkgsCross.${NIX_TARGET}.pkgsStatic.${PKG_NAME}" --impure \
--cores "$(($(nproc)+1))" --max-jobs "$(($(nproc)+1))" \
--log-format bar-with-logs --out-link "./TMPDIR"

#Copy (Dir may differ)
sudo rsync -av --copy-links "./TMPDIR/bin/." "./OUTDIR"
sudo chown -R "$(whoami):$(whoami)" "./OUTDIR" && chmod -R 755 "./OUTDIR"

#Strip & File
find "./OUTDIR" -type f -exec objcopy --remove-section=".comment" --remove-section=".note.*" "{}" \;
find "./OUTDIR" -type f ! -name "*.no_strip" -exec strip --strip-debug --strip-dwo --strip-unneeded --preserve-dates "{}" \;
find "./OUTDIR" -type f -print | xargs -I {} sh -c 'file {}; b3sum {}; sha256sum {}; du -sh {}'

#Cleanup
nix-collect-garbage >/dev/null 2>&1
```
{% endcode %}

