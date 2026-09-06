---
icon: github
description: Contribution guidelines
---

# Contribution

1. Read the [packaging section](../../packaging/), especially the [recipe reference](../../packaging/recipe.md) and the [examples](../../packaging/examples.md)
2. Look at [existing packages](https://github.com/pkgforge/soarpkgs/tree/main/packages) for something close to what you are adding
3. Scaffold the recipe, pin a version, and check it:

```bash
sbuild new mypkg owner/repo --type static
$EDITOR packages/mypkg/pkg.toml

sbuild resolve . mypkg
sbuild hashfill
sbuild validate
sbuild audit . mypkg --host x86_64-linux
```

4. Open a [pull request](https://github.com/pkgforge/soarpkgs/compare), or an [issue](https://github.com/pkgforge/soarpkgs/issues/new/choose) if you would rather someone else write it

`sbuild validate` is the gate in CI, so a branch that passes it locally will not fail there for a reason you could have seen. Commit both `pkg.toml` and the version file. A pinned URL without a hash beside it is the one state validation refuses.

We will help fix any mistakes and give feedback on the pull request. See [tooling](../../packaging/tooling.md) for what each command does and where to get `sbuild`.
