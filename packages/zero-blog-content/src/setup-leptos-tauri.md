## Setup Leptos + Tauri App (CSR - Client Side Rendering)

this does not include setting up rust or vscode, leave a comment for any requests you may have.

### LeptosFMT

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

### Issues

`Wrong MIME type for CSS stylesheet`, in `app.js` remove or comment this line

```
// <Stylesheet id="leptos" href="/pkg/tailwind.css"/>
```
