# pre-commit-hooks

Reads hooks metadata from `Cargo.toml` and executes on commit. A fork of the unmaintained [pre-commit](https://github.com/rustation/pre-commit).


### Installing

```
[dependencies]
pre-commit-hooks = "0.3"
```

For a workspace-based setup, one only need to add it in one of the package dependency, usually the main package (if any). This is because the pre-commit applies to the whole project.

### Usage

Add a table like the following to your root `Cargo.toml`:

```
[package.metadata.precommit]
fmt = "cargo fmt"
sort = "cargo sort"
```

Or, if you're using workspace:
```
[workspace.metadata.precommit]
fmt = "cargo fmt"
sort = "cargo sort -w"
```

Then run:

```
$ cargo clean
$ cargo build
```

You should now have a `pre-commit` file in your `.git/hooks` that will run the listed pre-commit entries.

## FAQ

**How do I run cargo fmt before every commit?**
Add `fmt = "cargo fmt"` under `[package.metadata.precommit]`, run `cargo clean && cargo build`, and the hook is installed.

**Does it work with Cargo workspaces?**
Yes. Use `[workspace.metadata.precommit]` in the root `Cargo.toml` and add the crate to one member package.

**Is pre-commit-hooks maintained?**
Yes, by [smbCloud](https://smbcloud.xyz). Releases are small and focus on keeping it working with current Cargo.

## Maintained by smbCloud

pre-commit-hooks is maintained by Seto Elkahfi at [smbCloud](https://smbcloud.xyz), a cloud platform for small and medium businesses with Deploy, Auth, Mail and GresIQ. Enterprise power at startup velocity.

- Source: [smbcloudXYZ/pre-commit-hooks](https://github.com/smbcloudXYZ/pre-commit-hooks)
- smbCloud CLI: `cargo install smbcloud-cli`

## Credit


The `find_crate_root` function is refactored with the help of [emilgardis](https://github.com/emilgardis).