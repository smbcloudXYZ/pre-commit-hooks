<!-- LOGO -->
<h1>
<p align="center">
  <img src="https://avatars.githubusercontent.com/u/89791739?s=200&v=4" alt="smbCloud Logo" width="128">
  <br>pre-commit-hooks
</h1>
  <p align="center">
    Run cargo fmt, clippy or any command as a git pre-commit hook, configured in Cargo.toml.
    <br />
    <br />
    <a href="https://smbcloud.xyz/">Website</a>
    ·
    <a href="https://github.com/smbcloudXYZ/pre-commit-hooks">Source</a>
    ·
    <a href="https://crates.io/crates/pre-commit-hooks">crates.io</a>
  </p>
  <p align="center">
    <a href="https://crates.io/crates/pre-commit-hooks"><img alt="Crates.io" src="https://img.shields.io/crates/v/pre-commit-hooks"></a>
    <a href="https://github.com/smbcloudXYZ/pre-commit-hooks/blob/main/LICENSE"><img alt="License" src="https://img.shields.io/github/license/smbcloudXYZ/pre-commit-hooks"></a>
  </p>

pre-commit-hooks reads hook commands from `Cargo.toml` and runs them on `git commit`. It works with Cargo workspaces. It is a fork of the unmaintained [pre-commit](https://github.com/rustation/pre-commit).

## Install

```toml
[dependencies]
pre-commit-hooks = "0.3"
```

In a workspace, add it to one package, usually the main one. The hook applies to the whole repository.

## Usage

Add a table like this to your root `Cargo.toml`:

```toml
[package.metadata.precommit]
fmt = "cargo fmt"
sort = "cargo sort"
```

For a workspace:

```toml
[workspace.metadata.precommit]
fmt = "cargo fmt"
sort = "cargo sort -w"
```

Then run:

```bash
cargo clean
cargo build
```

You now have a `pre-commit` file in `.git/hooks` that runs the listed entries.

## FAQ

**How do I run cargo fmt before every commit?**
Add `fmt = "cargo fmt"` under `[package.metadata.precommit]`, run `cargo clean && cargo build`, and the hook is installed.

**Does it work with Cargo workspaces?**
Yes. Use `[workspace.metadata.precommit]` in the root `Cargo.toml` and add the crate to one member package.

**Is pre-commit-hooks maintained?**
Yes, by [smbCloud](https://smbcloud.xyz). Releases are small and focus on keeping it working with current Cargo.

## About smbCloud

smbCloud is a cloud platform for small and medium businesses with Deploy, Auth, Mail and GresIQ. Enterprise power at startup velocity. Read the [docs](https://smbcloud.xyz/posts) or install the CLI with `cargo install smbcloud-cli`.

## Credit

Derived from [rustation/pre-commit](https://github.com/rustation/pre-commit) by Joe Grund. The `find_crate_root` function is refactored with the help of [emilgardis](https://github.com/emilgardis).

## License

[MIT](https://github.com/smbcloudXYZ/pre-commit-hooks/blob/main/LICENSE)

## Copyright

© 2026 Seto Elkahfi ([smbCloud](https://smbcloud.xyz)). Distributed by [Splitfire AB](https://5mb.app).
