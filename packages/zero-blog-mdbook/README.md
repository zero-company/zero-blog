## zero-blog

Open source blog for open source writers, no vendor locks, no paywalls, no strings attached.

### config

start command:

```
mdbook serve packages/zero-blog-mdbook -o
```

build command: specifically for cloudflare pages

```
sh -c "curl https://sh.rustup.rs -sSf | sh -s -- -y --default-toolchain none" && source ~/.cargo/env && rustup default stable && sh -c "curl https://rustwasm.github.io/wasm-pack/installer/init.sh -sSf | sh" && cargo install mdbook && mdbook build packages/zero-blog-mdbook
```

build output directory:

```
/packages/zero-blog-mdbook/dist
```

root directory:

```
/
```
