## zero-blog

Open source blog for open source writers, no vendor locks, no paywalls, no strings attached.

### config

install tools:

```
cargo install trunk
cargo install --force cargo-make
cargo install --locked wasm-bindgen-cli
pnpm add -g tailwindcss
rustup toolchain install nightly
rustup target add wasm32-unknown-unknown
```

start command:

```
trunk serve --open
```

clear space:
```
cargo clean
```