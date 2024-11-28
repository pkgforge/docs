---
description: Tests to perform after compiling a Binary
icon: vial-virus
---

# Build Tests

### [File](https://man7.org/linux/man-pages/man1/file.1.html)

{% code overflow="wrap" %}
```bash
!# Note: This is NOT as reliable as readelf (See Below)
file --print0 "$COMPILED_BINARY"
```
{% endcode %}

### [LDD](https://man7.org/linux/man-pages/man1/ldd.1.html)

{% code overflow="wrap" %}
```bash
!# Note: This is NOT as reliable as readelf (See Below)
# -d | --data-relocs --> Perform relocations and report any missing objects (ELF only).
# -r | --function-relocs --> Perform relocations for both data objects and functions, and report any missing objects or functions (ELF only).

ldd --data-relocs --function-relocs --verbose "$COMPILED_BINARY"
!# If this says `not a dynamic executable`, it's probably for another $ARCH (Verify Using file )

!# For aarch64 (binutils-aarch64-linux-gnu)
# -R | --dynamic-reloc --> Display the dynamic relocation entries in the file
# -T | --dynamic-syms --> Display the contents of the dynamic symbol table
aarch64-linux-gnu-objdump --dynamic-reloc --dynamic-syms "$COMPILED_BINARY" 
```
{% endcode %}

### [Mold](https://github.com/rui314/mold?tab=readme-ov-file#how-to-use)

{% code overflow="wrap" %}
```bash
!# This checks if mold was used as ld linker
readelf -p ".comment" "$COMPILED_BINARY"
# Note, use aarch64-linux-gnu-readelf (binutils-aarch64-linux-gnu) for aarch64
```
{% endcode %}

### [QEMU](https://www.unix.com/man-page/debian/1/qemu-user-static/)

{% code overflow="wrap" %}
```bash
!# This tests that the binary runs without `Segmentation Fault` | `Core Dumped` | `Illegal Instructions`
!# A chroot/proot could also be used
qemu-aarch64-static "$COMPILED_BINARY"
qemu-x86_64-static "$COMPILED_BINARY"
```
{% endcode %}

### [ReadELF](https://man7.org/linux/man-pages/man1/readelf.1.html)

{% code overflow="wrap" %}
```bash
!# Much more reliable than file/ldd
# -d | --dynamic  --> Checks Dynamic Section of the Binary [Look for NEEDED/Shared]
readelf --dynamic "$COMPILED_BINARY" | grep -i "NEEDED"
!# If this shows any `NEEDED` Section, it's not a Static Binary
# looks for the program interpreter section
# -p | --process-links '.interp' --> looks for the program interpreter section [Empty if it's really Static]
readelf -p '.interp' "$COMPILED_BINARY"
```
{% endcode %}

### Security

{% code overflow="wrap" %}
```bash
!# REF :: https://medium.com/@ofriouzan/part-1-introduction-and-basic-concepts-3a00105d7a13
          https://web.archive.org/web/20240210060942/https://medium.com/@ofriouzan/part-1-introduction-and-basic-concepts-3a00105d7a13
       :: https://medium.com/@ofriouzan/part-2-compiler-level-security-mechanisms-gcc-d01246b8d157
          https://web.archive.org/web/20240210060803/https://medium.com/@ofriouzan/part-2-compiler-level-security-mechanisms-gcc-d01246b8d157
       :: https://wiki.gentoo.org/wiki/GCC_optimization
       :: https://developers.redhat.com/articles/2022/06/02/use-compiler-flags-stack-protection-gcc-and-clang
       :: https://gcc.gnu.org/onlinedocs/gcc/Instrumentation-Options.html

!# Bare Minimum Sane Flags
-D_FORTIFY_SOURCE=2 (Add: CFLAGS | CXXFLAGS | CGO_CFLAGS)
 Not Relevant for musl libc : https://wiki.musl-libc.org/future-ideas
 Enables run-time buffer overflow detection, use -D_FORTIFY_SOURCE=1 if Program/Compilation Fails

-fcf-protection (GLIBC/GNU Only) --> Control Flow integrity protection  (Add: CFLAGS | CXXFLAGS | CGO_CFLAGS)

#https://gcc.gnu.org/onlinedocs/gcc/Instrumentation-Options.html#index-fcf-protection

-fstack-clash-protection --> Increased reliability of stack overflow detection  (Add: CFLAGS | CXXFLAGS | CGO_CFLAGS)
 #https://gcc.gnu.org/onlinedocs/gcc/Instrumentation-Options.html#index-fstack-clash-protection

-fstack-protector-strong (Add: CFLAGS | CXXFLAGS | CGO_CFLAGS)
 Balanced between -fstack-protector and -fstack-protector-all, the purpose of this option is to gain performance while sacrificing little security by broadening the scope of the stack protection without extending it to every function in the program.

!# RELRO (Mostly Relevant for Dynamically linked Binaries)
Relocation Read Only (RELRO) designating memory regions as read-only during the loading of a program, thwarting attempts by attackers to make runtime modifications.
-Wl,-z,relro --> Partial Relro (Add: LDFLAGS | extldflags | link-arg)
  Offers protection against runtime modifications to memory regions, safeguarding the integrity of the program, but the .got segment is not fully protected.

-Wl,-z,relro,-z,now --> Full Relro (Add: LDFLAGS | extldflags | link-arg)
 Offers enhanced security at the cost of a potentially longer load time for the process.

```
{% endcode %}

#### [HardeningMeter](https://github.com/OfriOuzan/HardeningMeter)

{% code overflow="wrap" %}
```bash
soar add "hardeningmeter#bin"
hardeningmeter -f "$COMPILED_BINARY" -s
!# Results: https://github.com/OfriOuzan/HardeningMeter/tree/main?tab=readme-ov-file#results
```
{% endcode %}

#### [hardening-check](https://manpages.debian.org/testing/devscripts/hardening-check.1.en.html)

{% code overflow="wrap" %}
```bash
!# sudo apt-install devscripts -y
hardening-check "$COMPILED_BINARY"
```
{% endcode %}
