## yarn, npm, pnpm

use storage
yarn cache clean
npm cache clean --force
cargo clean
pnpm store prune
C:\Users\jigzp\AppData\Local\pnpm\store\v3

https://github.com/npm/npm/issues/5706

https://github.com/npm/rfcs/issues/211
https://github.com/npm/rfcs/pull/217
https://github.com/npm/rfcs/pull/314

## pnpm nextjs

pnpm create next-app

## use turbo

https://github.com/vercel/turbo/issues/8553
gitignore, %SystemDrive% bug

## pnpm concurrently

"dev": "concurrently \"pnpm storybook:dev\" \"pnpm next:dev\" \"pnpm lib:dev\"",
"concurrently": "^8.2.2",

# pnpm nohoist, tailwindcss hoist bug

- try deleting node_modules, before installing clean

`pnpm install --shamefully-hoist`
public-hoist-pattern[]=!@types/react

## start project, clone project example subdirectory template

degit
pnpm create next-app new-next-app
pnpm dlx create-turbo@latest --example [example-name]
pnpm dlx degit https://github.com/payloadcms/payload-3.0-demo

# pnpx pnpm dlx fails to open package.json

reinstall node
Failed to create bin at

# update pnpm

corepack prepare pnpm@9.12.1 --activate

# npm.ps1 cannot be loaded because running scripts is disabled on this system