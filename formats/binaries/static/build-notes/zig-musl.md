---
description: https://ziglang.org/learn/overview/#zig-is-also-a-c-compiler
icon: z
---

# Zig (Musl)

{% code overflow="wrap" %}
```bash
!# REF :: https://andrewkelley.me/post/zig-cc-powerful-drop-in-replacement-gcc-clang.html
#      :: https://ziglang.org/learn/overview/#zig-is-also-a-c-compiler

❯ !# List Targets
zig targets | jq -r '.libc[]'

❯ !# Export Target
export ZIG_LIBC_TARGET="x86_64-linux-musl"
# Example: x86_64-linux-musl || aarch64-linux-musl

❯ !# Flags :: https://fig.io/manual/zig/cc
unset AR CC CFLAGS CXX CXXFLAGS DLLTOOL HOST_CC HOST_CXX LDFLAGS OBJCOPY RANLIB
export CC="zig cc -target $ZIG_LIBC_TARGET"
export CXX="zig c++ -target $ZIG_LIBC_TARGET"
export DLLTOOL="zig dlltool"
export HOST_CC="zig cc -target $ZIG_LIBC_TARGET"
export HOST_CXX="zig c++ -target $ZIG_LIBC_TARGET"
export OBJCOPY="zig objcopy"
export RANLIB="zig ranlib"
export CFLAGS="-O2 -flto=auto -fPIE -fpie -static -w -pipe ${CFLAGS}"
export CXXFLAGS="${CFLAGS}"
export LDFLAGS="-static -static-pie -pie -s -Wl,-S -Wl,--build-id=none ${LDFLAGS}"

❯ !# Make
make CFLAGS="$CFLAGS ${ADDITIONAL_ARGS}" CXXFLAGS="$CFLAGS ${ADDITIONAL_ARGS}" LDFLAGS="$LDFLAGS ${ADDITIONAL_ARGS}" --jobs="$(($(nproc)+1))" --keep-going
```
{% endcode %}
