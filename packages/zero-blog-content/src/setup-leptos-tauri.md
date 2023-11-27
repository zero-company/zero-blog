## Setup Leptos + Tauri App (CSR - Client Side Rendering)

this does not include setting up rust or vscode, leave a comment below for any requests you may have.

### Initialize Project

this is just a matter of preference, but we'll be using a monorepo structure.

```
packages/leptos-app
.gitignore
Cargo.toml
rust-toolchain.toml
```

`.gitignore`

```
target/
**/*.rs.bk
```

`Cargo.toml`

```
[workspace]
members = ["packages/*"]
resolver = "2"
```

`rust-toolchain.toml`

```
[toolchain]
channel = "nightly"
targets = ["wasm32-unknown-unknown"]
```

Inside `leptos-app`

```
public/favicon.svg
src
Cargo.toml
index.css
index.html
tailwind.config
Trunk.toml

```

`leptos-app/Cargo.toml`

```

```

### Setup Build Tool

```
cargo install trunk
```

alternatively you could use [https://github.com/leptos-rs/cargo-leptos](https://github.com/leptos-rs/cargo-leptos)

### Setup LeptosFMT

Use LeptosFMT to add formatting to leptos view! macro

```
cargo install leptosfmt
```

Add in `.vscode/settings.json`, recommend adding this setting only on workspaces using leptos

```
"rust-analyzer.rustfmt.overrideCommand": ["leptosfmt", "--stdin", "--rustfmt"]
```

Add `rustfmt.toml` to root

```
edition = "2021"
```

For more info visit: [https://github.com/bram209/leptosfmt](https://github.com/bram209/leptosfmt)

### Fix Issues

`Wrong MIME type for CSS stylesheet`, in `app.js` remove or comment this line

```
// <Stylesheet id="leptos" href="/pkg/tailwind.css"/>
```

### References/Resources

https://leptos-rs.github.io/leptos
https://github.com/leptos-rs/leptos/tree/main/examples
https://github.com/friendlymatthew/leptos-csr-tailwind
