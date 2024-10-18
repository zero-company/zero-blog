# rich text editors

- editorjs
  - no markdown support
- tinymce
  - paid markdown support
- froala
- tiptap
  - does not support markdown
- mdx-editor
- draft.js, dead
- quill
- lexical

- https://npmtrends.com/@editorjs/editorjs-vs-ckeditor5-vs-draft-js-vs-froala-editor-vs-prosemirror-model-vs-quill-vs-slate-vs-tinymce-vs-tiptap
- https://www.reddit.com/r/reactjs/comments/14s4mmh/which_rich_text_editor_to_use/

# ssg, frontend

- next
- solid
- vite
  https://trean.page/posts/2023-08-30-using-mdx-with-vite/

# state management, store management

- zustand, recommended
  - https://www.reddit.com/r/reactjs/comments/1ctsnov/why_choose_zustand_over_jotai/
- @preact/signals-react
  - https://github.com/preactjs/signals/issues/466
- jotai

# rest client

- swr
- tanstack-query, react-query
  - better than swr for mutation heavy api

# graphql client

- apollo client
- urql

# error handling

- http-status-codes 

# encryption

- bcrypt
- insecure, md5, sha-1
- sha-2

# git

- https://github.com/steveukx/git-js, simple-git, recommended
- https://github.com/creationix/js-git, dead
- https://github.com/nodegit/nodegit
- https://github.com/isomorphic-git/isomorphic-git

# cms

ORM:
- prisma
- kysely
- drizzle orm

SELF HOSTED:
- keystonejs, dead, deploy issues
- payload, bug can't create customId for seeding
- strapi

LOUD HOSTED:
- Sanity
- Storyblok
- DatoCMS
- Prismic
- GraphCMS
- Ghost
- Contentful
- Burdy

- https://www.reddit.com/r/nextjs/comments/svrznd/feedback_keystonejs_or_strapi_or_any_other/

# self hosted platform
- pocketbase
- appwrite.io
- coolify

# id
- uuid
- nanoid, can set custom length
- ulid
- snowflake id
- https://osamadev.medium.com/understanding-unique-identifiers-uid-uuid-guid-cuid-and-nano-id-3ef2d104ecdf

# auth

- next-auth, barely supports credentials
  - https://github.com/nextauthjs/next-auth/issues/3729
- lucia, dead
- passport
- ory, go fastest?
- keycloak, java startup time
- supertokens
- fusionauth, not open source
- better-auth

- https://supertokens.com/blog/self-hosted-authentication
- https://dev.to/supertokens/self-hosted-authentication-2bl2
- https://github.com/lucia-auth/lucia/discussions/1707#discussioncomment-10890390

# tunnel static ip

- https://free-for.dev/#/?id=tunneling-webrtc-web-socket-servers-and-other-routers

# misc

  - https://github.com/sindresorhus/slugify
  - https://github.com/dotenvx/dotenvx
  - https://github.com/ramda/ramda
  - https://github.com/lodash/lodash
  - https://codedamn.com/news/product/dont-use-prisma
  - Prisma Just Got a Lot Faster 
    https://www.youtube.com/watch?v=QwzulZEU0YA
  - https://github.com/date-fns/date-fns
  - https://github.com/enaqx/awesome-react