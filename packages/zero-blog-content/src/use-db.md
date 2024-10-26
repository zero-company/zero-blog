keystonejs, openapi swagger standardized rest api
payloadcms
datocms

seaorm
prisma

mongodb atlas, vendor locking, lack alternative hosts other than self hosting

schemaless postgresql, json

postgresql recursive delete foreign key constraints
do both filter out IDs pointing to nothing and clean up tables

https://www.sea-ql.org/Seaography/
https://blog.devgenius.io/seaography-a-quick-dive-into-graphql-for-rust-backend-development-14178b568860?gi=d7e94faae391

schema designing
figma
excalidraw

text editor
hide line breakpoints, glyph margin
hide line numbers, keep for easier resizing in touchscreen

https://dev.to/yexiyue/axumseaormasync-graphql-building-a-graphql-service-from-scratch-52kk
SeaORM - Introduction to Axum 0.5
https://www.youtube.com/watch?v=AWp-q95JGOM

redefine database
you don't store data in databases, you store indexes to data in database for faster filtering or searching

## use mongodb

delete deprecated unique indexes when removing unique fields

archiving guide to frozen slow backup database

## supabase

dbeaver ipv6 connection bug
https://github.com/orgs/supabase/discussions/4161
postgres://postgres.[MY-DATABASE]:[MY-PASSWORD]@aws-0-us-east-1.pooler.supabase.com:5432/postgres?connect_timeout=300
jdbc:postgresql://aws-0-ap-northeast-1.pooler.supabase.com:6543/postgres?user=postgres.rmhnigubqggewkayqsel&password=[YOUR-PASSWORD]
https://github.com/orgs/supabase/discussions/4161

https://dev.to/yexiyue/axumseaormasync-graphql-building-a-graphql-service-from-scratch-52kk
https://github.com/SeaQL/sea-orm/tree/master/examples/graphql_example
https://dev.to/aaronleopold/starter-axum-graphql-and-seaorm-template-3bnf
https://github.com/Colt45s/axum-graphql
https://github.com/SeaQL/sea-orm-tutorial/tree/master/graphql-example

mongodb id generator
https://observablehq.com/@hugodf/mongodb-objectid-generator
https://gist.github.com/solenoid/1372386

https://github.com/watscho/express-mongodb-rest-api-boilerplate

dry run graphql api database create for seeding if there are any id or unique field conflicts

# Print PostgreSQL version
SQL Editor
```
select
  version();
```
https://supabase.com/docs/guides/database/postgres/which-version-of-postgres

# git like immutable database history logging, audit

- Change Data Capture (CDC), Write-Ahead Logging (WAL)
- https://www.reddit.com/r/Database/comments/wrrw2e/how_would_you_guys_approach_a_history_table_its/
- How to use immudb, the lightweight, high-speed immutable database to store data PCI compliant
  https://www.youtube.com/watch?v=EUSoRUOy6cM
- PGaudit
- https://github.com/prisma/prisma/issues/1902
- https://medium.com/@arjunlall/prisma-audit-trail-guide-for-postgres-5b09aaa9f75a
- https://medium.com/@dev0jsh/implement-audit-trail-on-postgresql-with-prisma-orm-1c32afb44ebd