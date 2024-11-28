---
description: https://nim-lang.org/docs/nimc.html
icon: 'n'
---

# Nim

{% code overflow="wrap" %}
```bash
!# REF :: https://scripter.co/nim-deploying-static-binaries/
#      :: https://hookrace.net/blog/nim-binary-size/
nim --gcc.exe:musl-gcc --gcc.kinerexe:musl-gcc -d:release --opt:size --passL:-static c hello
```
{% endcode %}
