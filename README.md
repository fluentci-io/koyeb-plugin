# koyeb plugin

[![fluentci pipeline](https://shield.fluentci.io/x/koyeb)](https://pkg.fluentci.io/koyeb)
[![ci](https://github.com/fluentci-io/koyeb-plugin/actions/workflows/ci.yml/badge.svg)](https://github.com/fluentci-io/koyeb-plugin/actions/workflows/ci.yml)

This plugin sets up your CI/CD pipeline with a specific version of [koyeb cli](https://github.com/koyeb/koyeb-cli).

## 🚀 Usage

Add the following command to your CI configuration file:

```bash
fluentci run --wasm koyeb setup
```

## Functions

| Name   | Description                               |
| ------ | ----------------------------------------- |
| setup  | Installs a specific version of koyeb cli. |

## Code Usage

Add `fluentci-pdk` crate to your `Cargo.toml`:

```toml
[dependencies]
fluentci-pdk = "0.2.1"
```

Use the following code to call the plugin:

```rust
use fluentci_pdk::dag;

// ...

dag().call("https://pkg.fluentci.io/koyeb@v0.1.0?wasm=1", "setup", vec!["latest"])?;
```

## 📚 Examples

Github Actions:

```yaml
- name: Setup Fluent CI CLI
  uses: fluentci-io/setup-fluentci@v5
  with:
    wasm: true
    plugin: koyeb
    args: |
      setup
  env:
    GITHUB_ACCESS_TOKEN: ${{ secrets.GITHUB_TOKEN }}
- name: Show koyeb CLI version
  run: koyeb version
```
