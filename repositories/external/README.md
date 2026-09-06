---
icon: truck-clock
description: Third party and self hosted repositories
---

# Custom Repositories

[soarpkgs](../soarpkgs/) is the only repository PkgForge publishes, and Soar enables it by default. Soar is not tied to it, though. Any repository that publishes an index Soar can read works the same way, whether somebody else runs it or you do.

## Adding one

```bash
soar repo add myrepo "https://example.com/metadata-x86_64-linux.json"
soar sync
soar list myrepo
```

`soar repo` also has `update`, `remove` and `list`. Everything it does can be written straight into `~/.config/soar/config.toml` instead:

```toml
[[repositories]]
name = "myrepo"
url  = "https://example.com/metadata-x86_64-linux.json"
```

| Key | Default | Notes |
|---|---|---|
| `name` | required | How you refer to the repository, as in `soar list myrepo`. |
| `url` | required | The index. Must be `https`. |
| `pubkey` | none | Base64 minisign public key. |
| `signature_verification` | on when `pubkey` is set | Verify the index signature before using it. |
| `enabled` | `true` | Leave a repository configured without syncing it. |
| `desktop_integration` | `true` | Whether packages from here get desktop entries and icons. |
| `sync_interval` | `3h` | Also accepts `always` and `never`. |

{% hint style="warning" %}
A repository without a `pubkey` is unsigned, and Soar cannot tell you whether its index is the one its author published. Prefer one that signs, and pass the key when you add it.
{% endhint %}

## Running your own

An index is a JSON file, so hosting one is a matter of putting it somewhere reachable over `https`. Soar accepts:

* `.json`, the format described in [metadata](../soarpkgs/metadata.md)
* `.sdb`, the SQLite form, which `soar json2db` produces from the JSON
* either of those compressed with zstd

The SQLite form is worth generating if the repository is large, since Soar reads it directly instead of importing it on every sync.

The easiest way to produce one is the way soarpkgs does. Keep a tree of [declarative package definitions](../../packaging/), run [`sbuild meta`](../../packaging/tooling.md) over it per host, and publish the result:

```bash
sbuild meta --arch x86_64-linux --output metadata-x86_64-linux.json
soar json2db metadata-x86_64-linux.json metadata-x86_64-linux.sdb -r myrepo
zstd -19 metadata-x86_64-linux.sdb
```

Nothing requires that, however. The index is a plain format, and any generator that emits it will do.

## Signing

Sign each published file with [minisign](https://jedisct1.github.io/minisign/) and publish the `.sig` beside it, at the same URL with `.sig` appended:

```bash
minisign -S -s minisign.key -m metadata-x86_64-linux.sdb.zstd -x metadata-x86_64-linux.sdb.zstd.sig
```

Then hand out the public key with the repository, so users can add it:

```bash
soar repo add myrepo "https://example.com/metadata-x86_64-linux.sdb.zstd" --pubkey "RWQ..."
```
