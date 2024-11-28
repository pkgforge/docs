---
description: https://github.com/vlang/v/blob/master/README.md#docker-with-alpinemusl
icon: v
---

# Vlang

{% code overflow="wrap" %}
```bash
!#Sane CFLAGS
export CFLAGS="-O2 -flto=auto -static -w -pipe"
export CXXFLAGS="${CFLAGS}"

!#Sane LDFLAGS
export LDFLAGS="-static -s -Wl,-S -Wl,--build-id=none"

!#VFLAGS (v help build || v help build-c)
# -cc --> Compiler
# -gc --> Garbage-Collector
# -v  --> Enable verbosity in the V compiler while compiling
# -w  --> Hide Warning
# -prod --> Compile the executable in production mode, where most optimizations are enabled
# -compress --> Compress the compiled executable with UPX
# -showcc --> Prints the C command that is used to build the program.
# -o <output>, -output <output> --> Force V to output the executable in a specific location
# -skip-unused --> Skip generating C/JS code for unused functions
# -freestanding --> Build the executable without dependency on libc
# -os <os>, -target-os <os> -->
# android | dragonfly | freebsd | haiku | ios | linux | macos | netbsd | openbsd | plan9 | serenity | solaris | termux | vinix | wasm32 | wasm32-wasi | wasm32-emscripten | windows
export VFLAGS="-cc clang -gc none -w -prod -compress -showcc -cflags \"-O2\" -cflags \"-flto=auto\" -cflags \"-static\" -cflags \"-w\" -cflags \"-pipe\" -ldflags \"-static\" -ldflags \"-s\" -ldflags \"-Wl,--build-id=none\""

!# Build Script (build.vsh)
eval v "${VFLAGS}" run "./build.vsh"

!# Single SRC file
v -cc "clang" -gc "none" -w -prod -compress -showcc -cflags "-O2" -cflags "-flto=auto" -cflags "-static" -cflags "-w" -cflags "-pipe" -ldflags "-static" -ldflags "-s" -ldflags "-Wl,-S" -ldflags "-Wl,--build-id=none" "./path/to/v_src/dir" -o "./path/to/output"
#Or
eval v "${VFLAGS}" "./path/to/v_src/dir" -o "./path/to/output"
```
{% endcode %}
