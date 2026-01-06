---
icon: truck-clock
description: Custom Repositories
---

# External

Soar supports adding custom repositories. You can either use an existing third-party repo or build your own.

## Adding a Custom Repo

Edit `~/.config/soar/config.toml`:

```toml
[[repositories]]
name = "my-repo"
url = "https://example.com/metadata.json"
```

Then sync:

```bash
soar sync
soar list 'my-repo'
```

## Building Your Own Repo

To create a compatible repository, generate metadata in the same format as [soarpkgs metadata](../soarpkgs/metadata.md). Host the JSON file anywhere accessible via URL.
