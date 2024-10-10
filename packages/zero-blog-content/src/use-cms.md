keystonejs
payload cms
ghost cms
strapi cms

dato cms

https://www.reddit.com/r/nextjs/comments/10acm0j/best_self_hosting_cms/
https://github.com/payloadcms/payload/discussions/287

aws iam policy in expressjs
user group zeroid permission system, zero index data groups
importance of having a list of all active and inactive/disable access policies
default policy for all admins
policy name: AdminsCanReadOrDelete, list of admins zero-ids

# payload

Adding an ID into the data object on a "create" operation does not respect the ID inputted
https://github.com/payloadcms/payload/issues/6884

# graphql client like useswr

apollo client
urql
@graphql-codegen/cli
https://the-guild.dev/graphql/codegen/docs/getting-started

# keystonejs rest api

openapi swagger standardized rest api
https://github.com/keystonejs/keystone/discussions/7309

# prisma cloudflare worker

https://github.com/prisma/prisma/discussions/23762

# @prisma/client did not initialize yet

https://github.com/prisma/prisma/issues/21194
root non workspace .npmrc

```
public-hoist-pattern[]=*prisma*
```

https://github.com/keystonejs/keystone/issues/9208
https://github.com/keystonejs/keystone/issues/9349
https://github.com/prisma/prisma/issues/21194

```
pnpm why @prisma/client
```

remove carat from prisma dep version, use specific version

```
"prisma": "5.19.0",
"@prisma/client": "5.19.0",
"prisma": "^5.19.0",
"@prisma/client": "^5.19.0",
```
