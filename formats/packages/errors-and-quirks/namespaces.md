---
icon: shield-halved
description: Required for Sandboxing, Security & Performance
---

# Kernel User NameSpaces

{% hint style="info" %}
Required for Sandboxing, Security & Performance
{% endhint %}

Some portable packages use user namespaces for sandboxing, which may be restricted on certain systems.

## Common Errors

```
clone failed: Operation not permitted
```

```
user namespaces are not enabled
```

## Solutions

### Enable User Namespaces

**Check current setting:**
```bash
sysctl kernel.unprivileged_userns_clone
```

**Enable temporarily:**
```bash
sudo sysctl -w kernel.unprivileged_userns_clone=1
```

**Enable permanently:**
```bash
echo 'kernel.unprivileged_userns_clone=1' | sudo tee /etc/sysctl.d/userns.conf
sudo sysctl --system
```

### Debian/Ubuntu Specific

```bash
sudo sysctl -w kernel.apparmor_restrict_unprivileged_userns=0
```

### Use --no-sandbox

Some applications accept `--no-sandbox` flag (use with caution).
