---
description: https://doc.rust-lang.org/cargo/commands/cargo-build.html
icon: crab
---

# Cargo (Rust)

{% code overflow="wrap" %}
```bash
!# REF :: http://zderadicka.eu/static-build-of-rust-executables/
#      :: https://doc.rust-lang.org/rustc/codegen-options/index.html
#      :: https://msfjarvis.dev/posts/building-static-rust-binaries-for-linux/

❯ !# Check if there's feature tags 
# REF: https://doc.rust-lang.org/rustc/codegen-options/index.html#target-feature
rustc --print target-features

❯ !# Check for dependencies that dynamically link to libraries
# REF: https://msfjarvis.dev/posts/building-static-rust-binaries-for-linux/#other-potential-problems
cargo tree | grep -- -sys
# If the deps contain dynamic libs by default, using a custom Cargo.toml or build.rs sometimes work
# Cargo.toml :: https://msfjarvis.dev/g/androidx-release-watcher/b67a212106d8
# Build.rs   :: https://blog.davidvassallo.me/2021/06/10/lessons-learned-building-statically-linked-rust-binaries-openssl/
#            :: http://zderadicka.eu/static-build-of-rust-executables/

❯ !# List Targets
rustup target list

❯ !# Export Target
export RUST_TARGET="x86_64-unknown-linux-musl"
# Example: x86_64-unknown-linux-musl || aarch64-unknown-linux-musl

❯ !# Flags :: https://doc.rust-lang.org/cargo/reference/environment-variables.html
## So called codegen options are similar to CFLAGS/LDFLAGS, passed via -C as $RUSTFLAGS env 
# -C target-feature=+crt-static --> Statically Links the platform C library into the final binary
# -C default-linker-libraries=yes --> Linker Includes its default libraries. [Default is -nodefaultlibs | default-linker-libraries=no]
# -C link-self-contained=yes --> Uses only libraries/objects shipped with Rust [Max Protability]
# -C debuginfo=none --> no debug info at all [Turned on by default]
# -C strip=symbols --> strips debuginfo + symbols from the final binary
# -C prefer-dynamic=no --> use static linking (the default).
#
## Optimizations : https://doc.rust-lang.org/rustc/codegen-options/index.html#lto
# -C lto=yes --> uses link time optimizations, (Consumes Memory/RAM, also slower) [By default, set to thin]
#  This requires -C embed-bitcode=yes AND this will likely fail if RUST_TARGET="x86_64-unknown-linux-gnu"
# -C linker-plugin-lto=yes --> Enables linker plugin LTO. [Defers LTO optimizations to the linker]
# -C opt-level=3 --> Optimizes everything #https://doc.rust-lang.org/rustc/codegen-options/index.html#opt-level
#
## Linking :: https://doc.rust-lang.org/rustc/codegen-options/index.html#linker
#      REF :: https://github.com/rui314/mold?tab=readme-ov-file#how-to-use
# Uses mold as linker 🦠 , don't use this flags if default ld is preferred
# https://github.com/rui314/mold/blob/main/docs/mold.md
# -C linker=clang --> Clang instead of gcc/cc as otherwise -fuse-ld= would be treated as Unknown Arg
# -C link-arg=-fuse-ld=$(which mold) --> Uses Complete path to mold
# ⚠️⚠️ WARNING: pass these only if default LDFLAGS didn't work and mold has to be used specifically
#    Often these executables result in Segmentation Faults/Core Dumps
# ⚠️ -C link-arg=-Wl,--pie     --> Create a position-independent executable.
#    -C link-arg=-Wl,--Bstatic --> Do not link against shared libraries. (Similar to -no-pie)
#    -C link-arg=-Wl,--static  --> Do not link against shared libraries. (Similar to -static)
#    -C link-arg=-Wl,-S        --> Strips all symbol table and relocation information from the executable. (Similar to -s)
#    -C link-arg=-Wl,--build-id=none --> Embeds (md5 | sha1 | sha256 | uuid | 0x${hexstring} | none), default is sha1.
#
#   If mold is not used, then at least use:
#    -C link-args=-Wl,-S -C link-args=-Wl,--build-id=none --> Uses Default ld with Sane Opts

❯ !# static-pie + mold 🦠
unset AR CC CFLAGS CXX CXXFLAGS DLLTOOL HOST_CC HOST_CXX LDFLAGS OBJCOPY RANLIB
export RUSTFLAGS="-C target-feature=+crt-static -C default-linker-libraries=yes -C link-self-contained=yes -C prefer-dynamic=no -C embed-bitcode=yes -C lto=yes -C opt-level=3 -C debuginfo=none -C strip=symbols -C linker=clang -C link-arg=-fuse-ld=$(which mold) -C link-arg=-Wl,--Bstatic -C link-arg=-Wl,--pie -C link-arg=-Wl,--static -C link-arg=-Wl,-S -C link-arg=-Wl,--build-id=none"

❯ !# static(?pie) + mold 🦠
unset AR CC CFLAGS CXX CXXFLAGS DLLTOOL HOST_CC HOST_CXX LDFLAGS OBJCOPY RANLIB
export RUSTFLAGS="-C target-feature=+crt-static -C default-linker-libraries=yes -C link-self-contained=yes -C prefer-dynamic=no -C embed-bitcode=yes -C lto=yes -C opt-level=3 -C debuginfo=none -C strip=symbols -C linker=clang -C link-arg=-fuse-ld=$(which mold) -C link-arg=-Wl,--Bstatic -C link-arg=-Wl,--static -C link-arg=-Wl,-S -C link-arg=-Wl,--build-id=none"

❯ !# static(?pie) + No mold
unset AR CC CFLAGS CXX CXXFLAGS DLLTOOL HOST_CC HOST_CXX LDFLAGS OBJCOPY RANLIB
export RUSTFLAGS="-C target-feature=+crt-static -C default-linker-libraries=yes -C link-self-contained=yes -C prefer-dynamic=no -C embed-bitcode=yes -C lto=yes -C opt-level=3 -C debuginfo=none -C strip=symbols -C link-arg=-Wl,-S -C link-arg=-Wl,--build-id=none"

❯ !# Build :: https://doc.rust-lang.org/cargo/commands/cargo-build.html
rustup target add "$RUST_TARGET"
echo -e "\n[+]RUSTFLAGS: $RUSTFLAGS\n"
sed '/^\[profile\.release\]/,/^$/d' -i "./Cargo.toml" ; echo -e '\n[profile.release]\nstrip = true\nopt-level = 3\nlto = true' >> "./Cargo.toml"
cargo build --target "$RUST_TARGET" --release --jobs="$(($(nproc)+1))" --keep-going

#OUTPUT is usually in: "./target/$RUST_TARGET/release/"
# OR: cargo check --metadata-format="json" --quiet 
# --out-dir --> https://github.com/rust-lang/cargo/issues/6790

❯ !# NOTES on Selecting Features to be built
cargo metadata --no-deps --format-version 1 | jq -r ".packages[0].features | keys[]"
cargo metadata --no-deps --format-version 1 | jq ".packages[0].features | to_entries[]" | less
# This then can be used with cargo build --target "$RUST_TARGET" --no-default-features --features "$COMMA_LIST_OF_FEATURES" --release --jobs="$(($(nproc)+1))" --keep-going

❯ !# NOTES on *unknown-linux-gnu $RUST_TARGET
# Remove/Turn off the following:
#  -C link-self-contained=yes --> REMOVED || -C link-self-contained=yes
#  -C lto=yes --> REMOVED

❯ !# NOTES on using cross-rs : https://github.com/cross-rs/cross
# ❯ !# static(?pie) + No mold will work, but as soon as there's additional dependencies on things like openssl, it will fail
# Also, mold can't be used as linker
# Rather than cross, Use : https://hub.docker.com/r/azathothas/alpine-builder
```
{% endcode %}
