---
description: https://pkg.go.dev/cmd/go
icon: badger-honey
---

# GoLang

{% code overflow="wrap" %}
```bash
!# REF :: https://pkg.go.dev/cmd/go
#      :: https://mt165.co.uk/blog/static-link-go/
#      :: https://www.arp242.net/static-go.html
#      :: https://dubo-dubon-duponey.medium.com/a-beginners-guide-to-cross-compiling-static-cgo-pie-binaries-golang-1-16-792eea92d5aa
## https://go.dev/doc/install/source#environment
# GOARCH | GOOS --> go tool dist list [Lists All Targets operating systems and compilation architectures]
# GOARCH="amd64" GOOS="linux" --> x86_64 Linux
# GOARCH="arm64" GOOS="linux" --> aarch64 Linux
# CGO_ENABLED=0 --> Disables Linking against C libraries
#   This needs to be enabled sometimes, such sql libs, in such cases, it is also recommended to use CGO_CFLAGS (Same as CFLAGS)
#   CGO_ENABLED="1" CGO_CFLAGS="-O2 -static -w -pipe"
#
## -buildmode --> kind of object file is to be built (Help: go help buildmode )
# -buildmode=default --> Default, doesn't need to be specified
#    Listed main packages are built into executables and listed non-main packages are built into .a files
# -buildmode=exe --> Build the listed main packages and everything they import into executables. Packages not named main are ignored.
# -buildmode=pie --> Same as -buildmode=exe but position independent executables (PIE) 
#
## -gcflags --> compiler flags that can be passed to the Go compiler (go build | go install).
# REF : https://copyprogramming.com/howto/what-s-go-cmd-option-gcflags-all-possible-values
# Help : go tool compile -help
# ☣️ -N --> Disables optimizations. This is for Debug Builds
# ☣️ -l --> Disables inlining (Disables optimizations), also for Debug Builds
#   This reduces size, but at cost of optimization: https://github.com/xaionaro/documentation/blob/master/golang/reduce-binary-size.md
#
## https://pkg.go.dev/cmd/link
# -ldflags --> options passed to the Go linker (ld) during the build process
#    -buildid= --> Strips all buildids from executables
#    -s --> Omit the symbol table and debug information.
#    -w --> Omits the DWARF symbol table.
#
## go build -ldflags="-help" (Must have a .go file)
# -linkmode --> External (Requires CGO_ENABLED="1")
# -extld --> use linker when linking in external mode
# -extldflags flags --> pass flags to external linker
# Use mold as ld [https://github.com/rui314/mold/blob/main/docs/mold.md] 🦠
#  -ldflags="-buildid= -s -w -linkmode external -extld clang -extldflags '-static -s -fuse-ld=mold -Wl,--Bstatic -Wl,--static -Wl,-S -Wl,--build-id=none'"
#  # Using mold as ld, means no zig-musl
#
# ☣️ -a --> forces rebuilding of packages that are already up-to-date.
#    # This just wastes resources for no reason. go clean cache already gets rid of cache
#    # https://gcc.gnu.org/onlinedocs/gcc/Code-Gen-Options.html#index-fpic
# ☣️ -Og --> completely disables a number of optimization passes, meant for DEBUG builds
# ☣️ -g --> This option includes debugging information in the compiled executable
# 
# trimpath --> Removes all file system paths from the resulting executable
#   This sometimes causes weird behaviours: https://github.com/golang/go/issues/57328#issuecomment-1353330403
#
## go clean :: https://pkg.go.dev/cmd/go/internal/clean
# -cache --> Removes the entire go build cache (This already purges testcache, modcache & fuzzcache. Others are for redundancy)
# -testcache --> Expire all test results in the go build cache.
# -modcache --> Removes the entire module download cache + unpacked source code of versioned dependencies.
# -fuzzcache --> Removes files stored in the Go build cache for fuzz testing

!#ENV
export GOARCH="amd64" #arm64 (To list: go tool dist list)
export GOOS="linux" # (To list: go tool dist list)
export CGO_ENABLED="1" # To link against musl libc using zig OR build in pie mode
export CGO_CFLAGS="-O2 -flto=auto -fPIE -fpie -static -w -pipe"
export ZIG_LIBC_TARGET="x86_64-linux-musl"
export CC="zig cc -target $ZIG_LIBC_TARGET"
export CXX="zig c++ -target $ZIG_LIBC_TARGET"

❯ !# static-no-pie + stripped [Go Built-In] [RECOMMENDED]
# This produces smallest binaries & compiles the quickest
CGO_ENABLED="0" CC="" CXX="" go build -v -trimpath -ldflags="-buildid= -s -w -extldflags '-static'"

❯ !# static-pie + stripped [Go Built-In] [NOT-RECOMMENDED]
# This by default will link against shared libs from glibc (a bad idea) unless the Host is true musl only
# Binaries are larger in size & build/linking takes a long time
# Note: Multiple/Duplicatted -s -w -buildmode flags are specified as redundancy
CC="" CXX="" go build -v -trimpath -buildmode="pie" -ldflags="-s -w -buildid= -linkmode=external -extldflags '-s -w -static-pie -Wl,--build-id=none'"

❯ !# static-pie + stripped [zig musl] [RECOMMENDED]
# This links against bundled musl libc with zig.
# Binaries are larger in size & build/linking takes a long time
# Note: Multiple/Duplicatted -s -w -build-id flags are specified as redundancy
go build -v -trimpath -buildmode="pie" -ldflags="-s -w -buildid= -linkmode=external -extldflags '-s -w -static-pie -Wl,--build-id=none'"
```
{% endcode %}
